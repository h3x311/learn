# NextJs basic

## Navigation

- `Link`

## Layout

- `RootLayout`
- `{children}`

## Loading

- `loading.tsx`

## Image

### property
#### layout
- fill
  - 作为bg来填充容器
- fixed
  - 固定大小的图片
- responsive
  - 可以根据容器大小来调整
- intrinsic
  - 可以调整,不会超过原始的尺寸
#### objectFit
- cover
  - 会填满 但可能被裁剪
- contain
  - 尽可能保持比例,但可能留白
- fill
  - 会填满 但可能变形
- scale-down
  - 会缩减到最小,但不会裁剪,也不会比原来的大
- none
  - 保持原始尺寸
#### 本身的属性的例子
```tsx
  <Image
    src={logo}
    width={500}
    height={500}
    quality={100}
    alt="logo"
    placeholder="blur"
  />
```

#### 在外面套用div的例子
```tsx
<div className="relative aspect-square col-span-2">
  <Image
    src={logo}
    fill
    alt="logo"
    objectFit="contain"
    className="object-contain"
  />
</div>
```
