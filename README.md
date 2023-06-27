# 構成
- src/component/
- src/app/
- src/app/layout.tsx
- src/app/(common)/_component
- src/app/(common)/page.tsx
- src/feature
- src/common
- src/common/env/env.ts
- src/common/constant/constant.ts
- src/common/hooks
- src/common/hooks/use-xxx/use-xxx.ts
- src/icon
- src/lib
- src/util

## コロケーションについて
関心が同じものは同じ場所に置く(test,stories,scssなど)

- src/app/(common)/page.tsx
- src/app/(common)/page.spec.ts
- src/app/(common)/page.stories.tsx
- src/app/(common)/page.module.scss

- src/app/(common)/_component/component-name/component-name.tsx
- src/app/(common)/_component/component-name/component-name.spec.ts
- src/app/(common)/_component/component-name/component-name.stories.tsx
- src/app/(common)/_component/component-name/component-name.module.scss

- src/component/component-name/component-name.tsx
- src/component/component-name/component-name.spec.ts
- src/component/component-name/component-name.stories.tsx
- src/component/component-name/component-name.module.scss

## React Componentを置く場所について
React Componentは以下の3つの場所に置くことができる
- src/component
- src/app/_component
- src/feature

### src/component
src/componentには何にも依存していない純粋コンポーネントを置く
例: src/component/form/input/input.tsx

### src/app/_component
src/app/_componentにはpageに依存するcomponentを配置する
例: src/app/_component/page-deps-component/page-deps-component.tsx

### src/feature
src/featureにはドメインに依存するcomponentなどを配置する
例: 
- src/feature/user/create/create-user/create-user.tsx
- src/feature/user/create/create-user-modal/create-user-modal.tsx
- src/feature/user/create/use-create-user/use-create-user.ts

## フォルダ名/ファイル名
- 単数形で統一する
- ケバブケースで統一する
- コロケーションを意識する

```shell
src/app/component
```

```shell
src/app/component/component-name/component-name.tsx
src/app/component/component-name/component-name.spec.ts
src/app/component/component-name/component-name.stories.tsx
src/app/component/component-name/component-name.module.scss
```


## コンポーネント名
- named exportのArrow Functionの名前はPascalCaseで統一する
- ただしNext.jsの[File Conventions](https://nextjs.org/docs/app/api-reference/file-conventions)の場合はdefault exportの無名関数のfunctionで宣言する

### Arrow Function
```tsx
export const ComponentName = () => {
  return <div></div>
}
```

### Next.jsのFile Conventions
```tsx
export default function () {
  return <div></div>
}
```

```tsx
export default async function () {
  return <div></div>
}
```

## Props
- propsの方の名前はPropsにする
- propsの型はTypeで定義する
- ComponentPropsを使用して型を定義する
- 必要な型以外を受け取らないようにする

```tsx
type Props = Pick<ConmponentProps<'div'>,'className' | 'children'>

export const ComponentName = ({ children, className }: Props) => {
  return <div className={className}>{children}</div>
}
```