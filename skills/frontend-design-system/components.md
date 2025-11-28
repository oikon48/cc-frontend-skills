# Component Design Reference

このドキュメントでは、独自性のあるコンポーネント設計のガイドラインを提供します。

## Button Components

### 避けるべきパターン

```jsx
// ❌ 汎用的すぎる
<button className="bg-blue-500 text-white px-4 py-2 rounded">Click me</button>
```

### 推奨パターン

#### Brutalist Button

```jsx
<button
  className="
  relative px-8 py-4
  bg-black text-white font-bold uppercase tracking-wider
  border-4 border-black
  shadow-[4px_4px_0_0_#00FF88]
  hover:shadow-[8px_8px_0_0_#00FF88]
  hover:translate-x-[-4px] hover:translate-y-[-4px]
  transition-all duration-200
"
>
  Take Action
</button>
```

#### Organic Button

```jsx
<button
  className="
  px-8 py-4
  bg-gradient-to-br from-amber-100 to-orange-100
  text-amber-900 font-medium
  rounded-[60%_40%_30%_70%/60%_30%_70%_40%]
  border border-amber-200
  hover:shadow-lg hover:shadow-amber-200/50
  transition-all duration-300
"
>
  Explore Nature
</button>
```

#### Glassmorphic Button（控えめに使用）

```jsx
<button
  className="
  px-6 py-3
  bg-white/10 backdrop-blur-md
  text-white font-medium
  rounded-full
  border border-white/20
  hover:bg-white/20
  transition-all duration-300
"
>
  Discover More
</button>
```

---

## Card Components

### 独自性のあるカードパターン

#### Overlapping Card

```jsx
<div className="relative">
  {/* Background decorative element */}
  <div className="absolute -inset-2 bg-gradient-to-br from-primary/20 to-accent/20 rounded-3xl" />

  {/* Main card */}
  <div className="relative bg-white rounded-2xl p-8 shadow-xl">
    <div className="absolute -top-6 left-8">
      <span className="bg-accent text-white px-4 py-2 rounded-full text-sm font-medium">
        Featured
      </span>
    </div>
    <h3 className="text-2xl font-bold mt-4">Card Title</h3>
    <p className="text-gray-600 mt-2">Card description goes here.</p>
  </div>
</div>
```

#### Asymmetric Card

```jsx
<div
  className="
  bg-white rounded-tl-3xl rounded-br-3xl
  p-8 shadow-lg
  border-l-4 border-primary
  hover:translate-x-2 transition-transform
"
>
  <h3 className="text-xl font-bold">Asymmetric Design</h3>
  <p className="text-gray-600 mt-2">Breaking the symmetry rule.</p>
</div>
```

---

## Hero Sections

### 避けるべきレイアウト

```
[    Text     ] [   Image   ]  ← 50/50の均等分割
```

### 推奨レイアウト

#### Asymmetric Split

```
[  Text  ] [      Large Image      ]  ← 35/65の非対称
```

```jsx
<section className="grid grid-cols-[35fr_65fr] min-h-screen">
  <div className="flex flex-col justify-center px-12">
    <h1 className="text-6xl font-bold leading-tight">
      Breaking
      <br />
      Conventions
    </h1>
    <p className="text-xl text-gray-600 mt-6">
      Design that stands out from the crowd.
    </p>
  </div>
  <div className="relative overflow-hidden">
    <img src="hero.jpg" className="object-cover w-full h-full" />
    <div className="absolute inset-0 bg-gradient-to-r from-white via-transparent to-transparent" />
  </div>
</section>
```

#### Overlapping Elements

```jsx
<section className="relative min-h-screen flex items-center">
  {/* Background text */}
  <h1
    className="
    absolute left-0 top-1/2 -translate-y-1/2
    text-[20vw] font-black text-gray-100
    select-none pointer-events-none
  "
  >
    BOLD
  </h1>

  {/* Content */}
  <div className="relative z-10 max-w-2xl mx-auto text-center">
    <span className="text-primary font-medium tracking-widest uppercase">
      Welcome to
    </span>
    <h2 className="text-5xl font-bold mt-4">Something Different</h2>
  </div>
</section>
```

---

## Navigation Patterns

### Creative Navigation Ideas

#### Vertical Side Nav

```jsx
<nav
  className="
  fixed left-0 top-0 h-full w-20
  bg-gray-900 text-white
  flex flex-col items-center py-8
"
>
  <div className="flex-1 flex flex-col items-center space-y-8 mt-12">
    {navItems.map((item) => (
      <a
        key={item.id}
        className="
          group relative w-12 h-12
          flex items-center justify-center
          rounded-xl hover:bg-white/10
          transition-colors
        "
      >
        <Icon name={item.icon} />
        <span
          className="
          absolute left-full ml-4 px-3 py-1
          bg-gray-800 rounded text-sm whitespace-nowrap
          opacity-0 group-hover:opacity-100
          transition-opacity
        "
        >
          {item.label}
        </span>
      </a>
    ))}
  </div>
</nav>
```

#### Floating Navigation

```jsx
<nav
  className="
  fixed bottom-8 left-1/2 -translate-x-1/2
  bg-white/80 backdrop-blur-lg
  rounded-full px-8 py-4 shadow-lg
  border border-gray-200
"
>
  <ul className="flex items-center space-x-8">
    {navItems.map((item) => (
      <li key={item.id}>
        <a className="font-medium hover:text-primary transition-colors">
          {item.label}
        </a>
      </li>
    ))}
  </ul>
</nav>
```

---

## Animation Patterns

### Page Load Animation

```jsx
// Staggered fade-in for content sections
const containerVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.1,
      delayChildren: 0.2,
    },
  },
};

const itemVariants = {
  hidden: { opacity: 0, y: 20 },
  visible: {
    opacity: 1,
    y: 0,
    transition: {
      duration: 0.6,
      ease: [0.16, 1, 0.3, 1], // ease-out-expo
    },
  },
};
```

### Scroll-Triggered Animation

```jsx
// Intersection Observer pattern
const useScrollAnimation = () => {
  const ref = useRef(null);
  const [isVisible, setIsVisible] = useState(false);

  useEffect(() => {
    const observer = new IntersectionObserver(
      ([entry]) => setIsVisible(entry.isIntersecting),
      { threshold: 0.1, rootMargin: '-50px' },
    );
    if (ref.current) observer.observe(ref.current);
    return () => observer.disconnect();
  }, []);

  return { ref, isVisible };
};
```

---

## Micro-Interactions

### Button Hover Effect

```css
.button-magnetic {
  position: relative;
  transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.button-magnetic:hover {
  transform: scale(1.05);
}

.button-magnetic::after {
  content: '';
  position: absolute;
  inset: -10px;
  background: radial-gradient(
    circle at var(--x, 50%) var(--y, 50%),
    rgba(var(--accent-rgb), 0.15) 0%,
    transparent 70%
  );
  opacity: 0;
  transition: opacity 0.3s;
}

.button-magnetic:hover::after {
  opacity: 1;
}
```

### Input Focus Animation

```css
.input-animated {
  border: 2px solid transparent;
  background:
    linear-gradient(white, white) padding-box,
    linear-gradient(135deg, var(--primary), var(--accent)) border-box;
  background-size:
    100% 100%,
    0% 100%;
  background-position:
    0 0,
    0 100%;
  transition: background-size 0.3s ease;
}

.input-animated:focus {
  background-size:
    100% 100%,
    100% 100%;
  outline: none;
}
```
