# makeResponsive

## Specification

`makeResponsive` is a high-order component designed for providing [Responsive props](../../fundamentals/responsive-props.md) to any given React component.

### Alternative declaration

Apart from `makeResponsive`, you can use `useResponsiveProps` hooks to proxy a map of props and resolve them based on the current breakpoint.

{% code title="components/Image.jsx" %}
```jsx
import React from 'react'
import { useResponsiveProps } from 'atomic-layout'

export const Image = (props) => {
  const { url, size } = useResponsiveProps(props)
  return <img src={url} height={size} width={size} />
}
```
{% endcode %}

Such declaration, however, is lengthy and results into repeated logic when used frequently.

## Example

{% tabs %}
{% tab title="Image.jsx" %}
{% code title="components/Image.jsx" %}
```jsx
import React from 'react'
import { makeResponsive } from 'atomic-layout'

const Image = ({ url, size }) => (
  <img src={url} height={size} width={size} />
)

export default makeResponsive(Image)
```
{% endcode %}
{% endtab %}

{% tab title="Post.jsx" %}
```jsx
import React from 'react'
import Image from './Image'

const Post = () => (
  <Image
    src="mobile.jpg"
    srcMd="post-tablet.jpg"
    srcLg="post-large.jpg"
    size={50}
    sizeMd={75}
    sizeLg={125}
  />
)

export default Post
```
{% endtab %}
{% endtabs %}



