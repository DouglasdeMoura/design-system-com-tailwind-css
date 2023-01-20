---
# background: ./images/locus-design-system.jpg
class: text-center
highlighter: shiki
info: |
  ## Design System com Tailwind CSS
  Como criar um Design System com React e Tailwind CSS
drawings:
  persist: false
css: unocss
title: Design System com Tailwind CSS
titleTemplate: '%s | Douglas Moura'
lineNumbers: true
colorSchema: 'dark'
---

# Design System com Tailwind CSS

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/douglasdemoura" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
layout: center
---

# O que é um Design System?

<br>

Um **design system** é um conjunto de padrões usados para gerenciar o design
de uma organização em escala, utilizando componentes e orientações reutilizáveis.


<br>

<small>Isso não inclui apenas componentes visuais, mas também todo o posicionamento e a
comunicação da organização com seus clientes.</small>

<style>  
  p {
    color: white !important;
    font-size: 120%;
    line-height: 1.6;
  }
</style>

---
layout: center
---

# Por que usar um Design System?

- **Consistência** entre os produtos e canais de desenvolvimento de uma empresa;
- **Velocidade** na integração de novos membros ao time;
- **Padronização** de componentes e estilos, evitando a duplicação de código e iniciativas entre diferentes times.

---
layout: center
---

# Por que não usar um Design System?

- Equipe pequena;
- Custo de implementação, manutenção e atualização.

---
layout: center
---

# O desenvolvimento de um Design System exige que a organização seja <mark>madura e grande o suficiente</mark> para justificar o investimento.

---

# Quem está usando Design System?

- Google ([Material Design](https://m3.material.io/));
- IBM ([Carbon Design System](https://carbondesignsystem.com/));
- [Atlassian](https://atlassian.design/);
- [Governo do Brasil](https://www.gov.br/ds/home);
- [Governo dos EUA](https://designsystem.digital.gov/).

---
# Desenvolvimento de componentes

1. Escolha da tecnologia (React, Vue, Angular, WebComponents, etc);
2. Escolha do framework de estilos (Bootstrap, Tailwind, Material, etc).

---
# Componente: Botão

<div class="flex align-center justify-center mt-4">
  <video autoplay loop src="https://douglasmoura.dev/videos/storybook-button.mov"></video>
</div>

---

# Componente: Botão (React)

<br>
<br>

```tsx
import styles from './button.module.css'

type ButtonProps = {
  variant?: 'default' | 'primary' | 'secondary'
} & React.PropsWithChildren<React.ComponentPropsWithoutRef<'button'>>

export function Button({ children, variant, ...props}: ButtonProps) {
  return (
    <button data-variant={variant} className={styles.button} {...props}>
      {children}
    </button>
  )
}
```

---

# Componente: Botão (React)

<br>
<br>

```tsx {1,4,9}
import styles from './button.module.css'

type ButtonProps = {
  variant?: 'default' | 'primary' | 'secondary'
} & React.PropsWithChildren<React.ComponentPropsWithoutRef<'button'>>

export function Button({ children, variant, ...props}: ButtonProps) {
  return (
    <button data-variant={variant} className={styles.button} {...props}>
      {children}
    </button>
  )
}
```

---

# Componente: Botão (CSS)

```css {2-16} {maxHeight:'420px'}
.button {
  /* TODO: mover variáveis para global.css  */
  --font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --color-white: #fff;
  --color-black: #0f172a; /* slate-900 */
  --color-light-gray: #cbd5e1; /* slate-300 */
  --color-lighter-gray: #f1f5f9; /* slate-100 */
  --color-blue: #3b82f6; /* blue-500 */
  --color-dark-blue: #1d4ed8; /* blue-700 */
  --color-light-blue: #93c5fd; /* blue-300 */
  --color-lighter-blue: #eff6ff; /* blue-50 */
  --radius-sm: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;

  /* Variáveis do botão */
  --button-color: var(--color-black);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-light-gray);
  --button-border-color-hover: var(--color-lighter-gray);
  --button-outline-color-focus: var(--color-lighter-gray);

  all: unset;
  font-family: var(--font-family);
  background-color: var(--button-background-color);
  color: var(--button-color);
  border: 1px solid var(--button-border-color);
  border-radius: var(--radius-sm);
  padding: var(--spacing-sm) var(--spacing-md);
  cursor: pointer;
  user-select: none;
  line-height: 1;
}

.button:hover,
.button--state-hover {
  background-color: var(--button-border-color-hover);
}

.button:focus,
.button--state-focus {
  outline: 2px solid var(--button-outline-color-focus);
}

.button:active,
.button--state-active {
  margin-bottom: -2px;
}

.button:disabled,
.button--state-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button:disabled:hover,
.button--state-disabled:hover {
  background-color: var(--button-background-color);
}

.button[data-variant="primary"] {
  --button-color: var(--color-white);
  --button-background-color: var(--color-blue);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-dark-blue);
  --button-outline-color-focus: var(--color-light-blue);
}

.button[data-variant="secondary"] {
  --button-color: var(--color-blue);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-lighter-blue);
  --button-outline-color-focus: var(--color-light-blue);
}
```

<!-- Explicar as variáveis locais -->

---

# Componente: Botão (CSS)

```css {18-23} {maxHeight:'420px'}
.button {
  /* TODO: mover variáveis para global.css  */
  --font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --color-white: #fff;
  --color-black: #0f172a; /* slate-900 */
  --color-light-gray: #cbd5e1; /* slate-300 */
  --color-lighter-gray: #f1f5f9; /* slate-100 */
  --color-blue: #3b82f6; /* blue-500 */
  --color-dark-blue: #1d4ed8; /* blue-700 */
  --color-light-blue: #93c5fd; /* blue-300 */
  --color-lighter-blue: #eff6ff; /* blue-50 */
  --radius-sm: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;

  /* Variáveis do botão */
  --button-color: var(--color-black);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-light-gray);
  --button-border-color-hover: var(--color-lighter-gray);
  --button-outline-color-focus: var(--color-lighter-gray);

  all: unset;
  font-family: var(--font-family);
  background-color: var(--button-background-color);
  color: var(--button-color);
  border: 1px solid var(--button-border-color);
  border-radius: var(--radius-sm);
  padding: var(--spacing-sm) var(--spacing-md);
  cursor: pointer;
  user-select: none;
  line-height: 1;
}

.button:hover,
.button--state-hover {
  background-color: var(--button-border-color-hover);
}

.button:focus,
.button--state-focus {
  outline: 2px solid var(--button-outline-color-focus);
}

.button:active,
.button--state-active {
  margin-bottom: -2px;
}

.button:disabled,
.button--state-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button:disabled:hover,
.button--state-disabled:hover {
  background-color: var(--button-background-color);
}

.button[data-variant="primary"] {
  --button-color: var(--color-white);
  --button-background-color: var(--color-blue);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-dark-blue);
  --button-outline-color-focus: var(--color-light-blue);
}

.button[data-variant="secondary"] {
  --button-color: var(--color-blue);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-lighter-blue);
  --button-outline-color-focus: var(--color-light-blue);
}
```

<!-- Explicar as variáveis globais -->

---

# Componente: Botão (CSS)

```css {25-34} {maxHeight:'420px'}
.button {
  /* TODO: mover variáveis para global.css  */
  --font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --color-white: #fff;
  --color-black: #0f172a; /* slate-900 */
  --color-light-gray: #cbd5e1; /* slate-300 */
  --color-lighter-gray: #f1f5f9; /* slate-100 */
  --color-blue: #3b82f6; /* blue-500 */
  --color-dark-blue: #1d4ed8; /* blue-700 */
  --color-light-blue: #93c5fd; /* blue-300 */
  --color-lighter-blue: #eff6ff; /* blue-50 */
  --radius-sm: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;

  /* Variáveis do botão */
  --button-color: var(--color-black);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-light-gray);
  --button-border-color-hover: var(--color-lighter-gray);
  --button-outline-color-focus: var(--color-lighter-gray);

  all: unset;
  font-family: var(--font-family);
  background-color: var(--button-background-color);
  color: var(--button-color);
  border: 1px solid var(--button-border-color);
  border-radius: var(--radius-sm);
  padding: var(--spacing-sm) var(--spacing-md);
  cursor: pointer;
  user-select: none;
  line-height: 1;
}

.button:hover,
.button--state-hover {
  background-color: var(--button-border-color-hover);
}

.button:focus,
.button--state-focus {
  outline: 2px solid var(--button-outline-color-focus);
}

.button:active,
.button--state-active {
  margin-bottom: -2px;
}

.button:disabled,
.button--state-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button:disabled:hover,
.button--state-disabled:hover {
  background-color: var(--button-background-color);
}

.button[data-variant="primary"] {
  --button-color: var(--color-white);
  --button-background-color: var(--color-blue);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-dark-blue);
  --button-outline-color-focus: var(--color-light-blue);
}

.button[data-variant="secondary"] {
  --button-color: var(--color-blue);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-lighter-blue);
  --button-outline-color-focus: var(--color-light-blue);
}
```

<!-- Explicar as variáveis locais -->

---

# Componente: Botão (CSS)

```css {37-61} {maxHeight:'420px'}
.button {
  /* TODO: mover variáveis para global.css  */
  --font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --color-white: #fff;
  --color-black: #0f172a; /* slate-900 */
  --color-light-gray: #cbd5e1; /* slate-300 */
  --color-lighter-gray: #f1f5f9; /* slate-100 */
  --color-blue: #3b82f6; /* blue-500 */
  --color-dark-blue: #1d4ed8; /* blue-700 */
  --color-light-blue: #93c5fd; /* blue-300 */
  --color-lighter-blue: #eff6ff; /* blue-50 */
  --radius-sm: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;

  /* Variáveis do botão */
  --button-color: var(--color-black);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-light-gray);
  --button-border-color-hover: var(--color-lighter-gray);
  --button-outline-color-focus: var(--color-lighter-gray);

  all: unset;
  font-family: var(--font-family);
  background-color: var(--button-background-color);
  color: var(--button-color);
  border: 1px solid var(--button-border-color);
  border-radius: var(--radius-sm);
  padding: var(--spacing-sm) var(--spacing-md);
  cursor: pointer;
  user-select: none;
  line-height: 1;
}

.button:hover,
.button--state-hover {
  background-color: var(--button-border-color-hover);
}

.button:focus,
.button--state-focus {
  outline: 2px solid var(--button-outline-color-focus);
}

.button:active,
.button--state-active {
  margin-bottom: -2px;
}

.button:disabled,
.button--state-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button:disabled:hover,
.button--state-disabled:hover {
  background-color: var(--button-background-color);
}

.button[data-variant="primary"] {
  --button-color: var(--color-white);
  --button-background-color: var(--color-blue);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-dark-blue);
  --button-outline-color-focus: var(--color-light-blue);
}

.button[data-variant="secondary"] {
  --button-color: var(--color-blue);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-lighter-blue);
  --button-outline-color-focus: var(--color-light-blue);
}
```

<!-- Explicar as variáveis locais -->

---

# Componente: Botão (CSS)

```css {63-77} {maxHeight:'420px'}
.button {
  /* TODO: mover variáveis para global.css  */
  --font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif,
    "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  --color-white: #fff;
  --color-black: #0f172a; /* slate-900 */
  --color-light-gray: #cbd5e1; /* slate-300 */
  --color-lighter-gray: #f1f5f9; /* slate-100 */
  --color-blue: #3b82f6; /* blue-500 */
  --color-dark-blue: #1d4ed8; /* blue-700 */
  --color-light-blue: #93c5fd; /* blue-300 */
  --color-lighter-blue: #eff6ff; /* blue-50 */
  --radius-sm: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;

  /* Variáveis do botão */
  --button-color: var(--color-black);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-light-gray);
  --button-border-color-hover: var(--color-lighter-gray);
  --button-outline-color-focus: var(--color-lighter-gray);

  all: unset;
  font-family: var(--font-family);
  background-color: var(--button-background-color);
  color: var(--button-color);
  border: 1px solid var(--button-border-color);
  border-radius: var(--radius-sm);
  padding: var(--spacing-sm) var(--spacing-md);
  cursor: pointer;
  user-select: none;
  line-height: 1;
}

.button:hover,
.button--state-hover {
  background-color: var(--button-border-color-hover);
}

.button:focus,
.button--state-focus {
  outline: 2px solid var(--button-outline-color-focus);
}

.button:active,
.button--state-active {
  margin-bottom: -2px;
}

.button:disabled,
.button--state-disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button:disabled:hover,
.button--state-disabled:hover {
  background-color: var(--button-background-color);
}

.button[data-variant="primary"] {
  --button-color: var(--color-white);
  --button-background-color: var(--color-blue);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-dark-blue);
  --button-outline-color-focus: var(--color-light-blue);
}

.button[data-variant="secondary"] {
  --button-color: var(--color-blue);
  --button-background-color: var(--color-white);
  --button-border-color: var(--color-blue);
  --button-border-color-hover: var(--color-lighter-blue);
  --button-outline-color-focus: var(--color-light-blue);
}
```

<!-- Explicar as variáveis locais -->

---

# Componente: Botão (Tailwind CSS)

```tsx {1,2} {maxHeight:'420px'}
import { cva } from 'class-variance-authority'
import { twMerge } from 'tailwind-merge'

type ButtonProps = {
  variant?: 'default' | 'primary' | 'secondary'
} & React.PropsWithChildren<React.ComponentPropsWithoutRef<'button'>>

const buttonVariants = cva(
  [
    'py-2',
    'px-4',
    'border',
    'rounded',
    'cursor-pointer',
    'select-none',
    'leading-4',
    'disabled:opacity-50',
    'disabled:cursor-not-allowed',
  ],
  {
    variants: {
      intent: {
        default: [
          'bg-white',
          'text-black',
          'border-slate-300',
          'hover:bg-slate-100',
          'focus:ring-2',
          'focus:ring-slate-300',
          'disabled:hover:bg-white',
        ],
        primary: [
          'bg-blue-500',
          'text-white',
          'border-blue-500',
          'hover:bg-blue-700',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-blue-500',
        ],
        secondary: [
          'bg-white',
          'text-blue-500',
          'border-blue-500',
          'hover:bg-blue-50',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-white',
        ],
      },
    },
    defaultVariants: {
      intent: 'default',
    },
  }
)

const buttonStyles = (variant: ButtonProps['variant']) =>
  twMerge(buttonVariants({ intent: variant }))

export function Button({
  children,
  variant = 'default',
  ...props
}: ButtonProps) {
  return (
    <button className={buttonStyles(variant)} {...props}>
      {children}
    </button>
  )
}
```

---

# Componente: Botão (Tailwind CSS)

```tsx {8-56} {maxHeight:'420px'}
import { cva } from 'class-variance-authority'
import { twMerge } from 'tailwind-merge'

type ButtonProps = {
  variant?: 'default' | 'primary' | 'secondary'
} & React.PropsWithChildren<React.ComponentPropsWithoutRef<'button'>>

const buttonVariants = cva(
  [
    'py-2',
    'px-4',
    'border',
    'rounded',
    'cursor-pointer',
    'select-none',
    'leading-4',
    'disabled:opacity-50',
    'disabled:cursor-not-allowed',
  ],
  {
    variants: {
      intent: {
        default: [
          'bg-white',
          'text-black',
          'border-slate-300',
          'hover:bg-slate-100',
          'focus:ring-2',
          'focus:ring-slate-300',
          'disabled:hover:bg-white',
        ],
        primary: [
          'bg-blue-500',
          'text-white',
          'border-blue-500',
          'hover:bg-blue-700',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-blue-500',
        ],
        secondary: [
          'bg-white',
          'text-blue-500',
          'border-blue-500',
          'hover:bg-blue-50',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-white',
        ],
      },
    },
    defaultVariants: {
      intent: 'default',
    },
  }
)

const buttonStyles = (variant: ButtonProps['variant']) =>
  twMerge(buttonVariants({ intent: variant }))

export function Button({
  children,
  variant = 'default',
  ...props
}: ButtonProps) {
  return (
    <button className={buttonStyles(variant)} {...props}>
      {children}
    </button>
  )
}
```

---

# Componente: Botão (Tailwind CSS)

```tsx {58,59,67-69} {maxHeight:'420px'}
import { cva } from 'class-variance-authority'
import { twMerge } from 'tailwind-merge'

type ButtonProps = {
  variant?: 'default' | 'primary' | 'secondary'
} & React.PropsWithChildren<React.ComponentPropsWithoutRef<'button'>>

const buttonVariants = cva(
  [
    'py-2',
    'px-4',
    'border',
    'rounded',
    'cursor-pointer',
    'select-none',
    'leading-4',
    'disabled:opacity-50',
    'disabled:cursor-not-allowed',
  ],
  {
    variants: {
      intent: {
        default: [
          'bg-white',
          'text-black',
          'border-slate-300',
          'hover:bg-slate-100',
          'focus:ring-2',
          'focus:ring-slate-300',
          'disabled:hover:bg-white',
        ],
        primary: [
          'bg-blue-500',
          'text-white',
          'border-blue-500',
          'hover:bg-blue-700',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-blue-500',
        ],
        secondary: [
          'bg-white',
          'text-blue-500',
          'border-blue-500',
          'hover:bg-blue-50',
          'focus:ring-2',
          'focus:ring-blue-300',
          'disabled:hover:bg-white',
        ],
      },
    },
    defaultVariants: {
      intent: 'default',
    },
  }
)

const buttonStyles = (variant: ButtonProps['variant']) =>
  twMerge(buttonVariants({ intent: variant }))

export function Button({
  children,
  variant = 'default',
  ...props
}: ButtonProps) {
  return (
    <button className={buttonStyles(variant)} {...props}>
      {children}
    </button>
  )
}
```

---
layout: center
---

# Vantagens

- Isomorfismo: não há risco do uso de tamanhos ou cores erradas em diferentes partes do código;
- Velocidade: menos código para escrever e manter;

---

# Obrigado!

<div class="flex align-center w-full justify-between">
  <div class="flex flex-col gap-2 align-center justify-center">
    <div class="flex gap-2 align-center"><uim-twitter class="text-blue-400" /> <a href="https://twitter.com/douglasdemoura">@douglasdemoura</a></div>
    <div class="flex gap-2 align-center"><uim-instagram class="text-blue-400" /> <a href="https://instagram.com/douglasdemoura">@douglasdemoura</a></div>
    <div class="flex gap-2 align-center"><uim-arrow-up-right class="text-blue-400" /><a href="https://douglasmoura.dev">douglasmoura.dev</a></div>
  </div>
  <div class="flex flex-col align-center justify-center">
    <img src="https://www.gravatar.com/avatar/997c72f0b7ca0fc26bdf60ca27cb4194?s=350" alt="Douglas Moura" class="rounded-full ring-4 ring-white">
  </div>
</div>

---

# Referências

- [Reimagining Design Systems at Spotify](https://spotify.design/article/reimagining-design-systems-at-spotify);
- [Building a Visual Language](https://airbnb.design/building-a-visual-language/);
- [Design Systems 101](https://www.nngroup.com/articles/design-systems-101/);
- [Design Systems Handbook](https://www.designbetter.co/design-systems-handbook).