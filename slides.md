---
background: ./images/locus-design-system.jpg
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

# Por que usar um Design System?

- **Consistência** entre os produtos e canais de desenvolvimento de uma empresa;
- **Velocidade** na integração de novos membros ao time;
- **Padronização** de componentes e estilos, evitando a duplicação de código e iniciativas entre diferentes times.

---

# Por que não usar um Design System?

- Equipe pequena;
- Custo de implementação, manutenção e atualização.

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
  <video autoplay loop src="videos/storybook-button.mov"></video>
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

```tsx {1,4,10}
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
# CSS
---

# Referências

- [Reimagining Design Systems at Spotify](https://spotify.design/article/reimagining-design-systems-at-spotify);
- [Building a Visual Language](https://airbnb.design/building-a-visual-language/);
- [Design Systems 101](https://www.nngroup.com/articles/design-systems-101/);
- [Design Systems Handbook](https://www.designbetter.co/design-systems-handbook).