<h1>Focus ring - How to use</h1>

<section data-section="how-to-use">
  
  <p class="dummy-paragraph">The suggested way to apply a "focus-ring" style to an UI element is using the specific
    <strong>design token</strong>
    provided as CSS custom property.</p>

  <h4 class="dummy-h4">Design tokens</h4>
  <p class="dummy-paragraph">You can use the
    <code class="dummy-code">--token-focus-ring-action-box-shadow</code>
    <a href="./tokens">design token</a>
    directly in your CSS definitions:</p>
  
  <!-- prettier-ignore-start -->
```css
.your-selector {
  [...your CSS declarations]
  &:focus,
  &:focus-visible {
    box-shadow: var(--token-focus-ring-action-box-shadow);
  }
}
```
<!-- prettier-ignore-end -->

  
  <p class="dummy-paragraph"><strong>🚨 IMPORTANT: 🚨</strong></p>
  <ul>
    <li class="dummy-paragraph">the design token as CSS variable can be used
      <strong>only</strong>
      with a
      <code class="dummy-code">box-shadow</code>
      property</li>
    <li class="dummy-paragraph">the border radius depends on the UI element to which is applied to, so it's up to you to
      apply the right
      <code class="dummy-code">border-radius</code>
      (tip: consider to use the
      <code class="dummy-code">inherit</code>
      value).</li>
  </ul>

  <h4 class="dummy-h4">CSS helper classes</h4>
  <p class="dummy-paragraph">We provide also a
    <strong>CSS helper class</strong>
    <code class="dummy-code">.hds-focus-ring-box-shadow</code>, that is a wrapper of the design token above, but it's
    unlikely you can use it directly in a template, since this style is connected to the "focused" pseudo-state of an
    element (more likely it would be used in composition with other classes).</p>
  <p class="dummy-paragraph">To use this class you have to import the CSS file
    <code class="dummy-code">[products|devdot]/css/helpers/focus-ring.css</code>
    from the
    <code class="dummy-code">@hashicorp/design-system-tokens</code>
    package.</p>
  <p class="dummy-paragraph"><strong>🚨 IMPORTANT: 🚨</strong></p>
  <ul>
    <li class="dummy-paragraph">the border radius depends on the UI element to which is applied to, so it's up to you to
      apply the right
      <code class="dummy-code">border-radius</code>
      (tip: consider to use the
      <code class="dummy-code">inherit</code>
      value).</li>
  </ul>

  <h4 class="dummy-h4">Sass mixins</h4>
  <p class="dummy-paragraph">We have also created two
    <strong>Sass mixins</strong>
    <code class="dummy-code">hds-focus-ring-basic</code>
    and
    <code class="dummy-code">hds-focus-ring-with-pseudo-element</code>
    but they're mainly used for internal use (to the design system codebase). These mixins do more than just apply the
    focus style: they also take care of all the different way to declare the
    <code class="dummy-code">:focus/:focus-visible</code>
    for different browsers.
  </p>
  <p class="dummy-paragraph">To use these mixins you have to import the Sass file
    <code class="dummy-code">packages/components/app/styles/mixins/_focus-ring.scss</code>
    contained in the
    <code class="dummy-code">@hashicorp/design-system</code>
    monorepo or the same file
    <code class="dummy-code">app/styles/mixins/_focus-ring.scss</code>
    distributed in the
    <code class="dummy-code">@hashicorp/design-system-components</code>
    package.</p>
  <p class="dummy-paragraph">Then the mixins can be invoked in this way:</p>
  
  <!-- prettier-ignore-start -->
```css
/* include the mixin file via @use (path will depend on your context) */
@use '../mixins/focus-ring' as *;

/* apply the focus-ring as box-shadow ('action' will be the default color ) */
.your-selector {
  [...your CSS declarations]
  @include hds-focus-ring-basic();
}

/* apply the focus-ring as pseudo-element (with 'critical' color ) */
.your-selector {
  [...your CSS declarations]
  @include hds-focus-ring-with-pseudo-element($top: 0, $right: 0, $bottom: 0, $left: 0, $radius: 5px, $color: critical);
}
```
<!-- prettier-ignore-end -->

  

</section>