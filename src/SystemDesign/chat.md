# Requirements
## Core
- send a message to a user
- receive a message from a user
- see one's chat history with a user

## real time?
- users should be able to see each other's messages in real time without refreshing the page

## support which format of message?
- support text with emojis, discuss image later

## Does the app support offline mode?
- outgoing messages should be saved locally
- incoming messages should be saved locally
- when the app is offline, the user should be able to see the messages he/she has sent

## Does the app support multiple users?
- we can assume 1:1 msg service

# Architecture

## Tricky scenarios

- using the application on different tabs in same browser
- Using the application on different devices/browsers
- Offline mode
  - Outgoing messages should be retried when the app is online
  - if its too long ago, no longer makes sense to retry it.

## Client-side Database

- can solve diff tabs in same browser

## Data Syncer

Msg status
- sending
- sent
- delivered
- read
- failed

## Rendering

- highly interactive
- accessed when logged in
- do not need to be indexed by search engine
- fast initial load speed

- client-side rendering and single-page application
- server-side rendering (SSR) with client-side hydration(Dont need SEO Friendly)


# Data model

## Client-side Database

- Conversation - Conversation List
- Msg - Conversation 
- User - ALL
- ConversationUser
- DraftMsg - Conversation - 
- SendMSgRequest  - Msg Scheduler - (pending, in_flight, fail, success)
> DraftMsg and SendMSgRequest should be in client db for session synchronization

## Client-only state

- Selected conversation
- conversation scroll position
- conversation outgoing msg

# API 

## send msg

- msg --> sending
- sendMsgRequest --> pending
- UI --> sending
- DraftMsg <-- deleted
- MsgScheduler --> syncing `pending` with the server

## sync outgoing msg

> Msg scheduler should monitor the table of outgoing msg.
- pending --> in_flight
- in_flight --> check timestamp
  - check the last_send_at timestamp, if exceed, updated to fail, and fail_count by 1
- fail 
  - retry after a while, delay duration will increase exponentially with fail_count
  
## server events

### msg sent
- update message status to `sent`
- clean up this msg in msg scheduler
  - remove msg in sendMsgRequest table, no longer pending or inflight
  - remove any tasks in the task queue
- update UI

### msg delivered
- update message status to `delivered`
- update UI

### msg failed

- updated status in `sendMsgRequest` to fail, and fail_count by 1
  - we don't need to modify msg table to status fail, until we retry it again
- update UI

### incoming_msg 

- Append new msg into `Message` table
  - Create a new row in `conversation`
  - create a new row for msg's sender into `User` table if not exist
- Update UI

### sync
- First connect to server
  - Client's last update timestamp
  - Each conversation's cursor


## fetch conversations
- 

## fetch conversation msgs

# Optimization

## Client side DB
- use indexedDB
- sync across tabs
  - BroadcastChannel

### problem syncy between client and server

- out of order msg
- fetch new msgs
- send out pending msgs
- unsupported environment like private
- storage limits

### real time updates
- short polling
- long polling
- web sockets

## Network
- offline
  - add msg into `sendMsgRequest`
- Failures
  - failed msgs should be retried later
- Batching
- out of order
- disconnection

## Performance
- Lazy load components dont need for initial load(popmodels and emoji picker)
- windowing/virtualization for long list of messages 

## Accessibility

- Msg composer
  - Enter
  - shift+enter
- Between conversations
  - search bar
  - cmd + up/down
  - cmd + number

## offline support
- PWAs(Progressive Web Apps) use service workers to cache assets

## User experience

### Maintain scroll position
recalculate scroll position when new messages arrive
- new messages inserted at below
- above(search history)
- window resizing
- fixed height placeholder to rendering