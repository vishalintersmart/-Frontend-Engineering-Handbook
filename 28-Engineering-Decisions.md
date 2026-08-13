# Engineering Decisions

## Containers

Use

576 → 540

768 → 720

992 → 960

1200 → 1140

1440 → 1320

1600 → 1480

1920 → 1680

---

## Section IDs

Use kebab-case

about-us

our-services

contact-form

---

## Section Classes

Use camelCase

aboutSection

servicesSection

contactSection

---

## Page Wrapper

Always

<main id="pageWrapper" class="aboutPage">

---

## Images

Always include

width

height

alt

loading

decoding

fetchpriority (hero only)

---

## Hero Images

Never lazy-load

---

## JavaScript

Shared → assets/js/app.js

Page-specific → pageWrapper scoped

---

## CMS

Wrapper-based styling only