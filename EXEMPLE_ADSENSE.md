# 📝 Exemple d'intégration AdSense

## Voici comment intégrer AdSense dans vos pages :

### 1. Dans la page Blog (src/routes/blog/+page.svelte)

```svelte
<script lang="ts">
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import LoadingSpinner from '$lib/components/LoadingSpinner.svelte';
  import AdSense from '$lib/components/AdSense.svelte';  // ← AJOUTER CETTE LIGNE
  
  // ... votre code existant ...
</script>

<div class="min-h-screen bg-gray-50">
  <!-- Hero Section -->
  <section class="bg-gradient-to-r from-blue-600 to-purple-600 text-white py-20">
    <!-- ... votre hero existant ... -->
  </section>
  
  <!-- ANNONCE 1: En haut après le hero -->
  <div class="container mx-auto px-4 my-8">
    <AdSense 
      client="ca-pub-VOTRE_ID_ADSENSE"
      slot="1234567890"
      format="horizontal"
      style="display:block; text-align:center;"
    />
  </div>
  
  <!-- Filter Tags -->
  <section class="py-8 bg-white border-b border-gray-200">
    <!-- ... vos filtres existants ... -->
  </section>
  
  <!-- Blog Posts -->
  <section class="py-16">
    <div class="container mx-auto px-4">
      {#if loading}
        <!-- ... loading spinner ... -->
      {:else}
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          {#each filteredPosts as post, index}
            <article>
              <!-- ... votre article existant ... -->
            </article>
            
            <!-- ANNONCE 2: Après chaque 3ème article -->
            {#if (index + 1) % 3 === 0 && index < filteredPosts.length - 1}
              <div class="col-span-1 md:col-span-2 lg:col-span-3 my-8">
                <AdSense 
                  client="ca-pub-VOTRE_ID_ADSENSE"
                  slot="0987654321"
                  format="fluid"
                  style="display:block;"
                />
              </div>
            {/if}
          {/each}
        </div>
      {/if}
    </div>
  </section>
</div>
```

---

### 2. Dans la page d'accueil (src/routes/+page.svelte)

```svelte
<script>
  import AdSense from '$lib/components/AdSense.svelte';
</script>

<!-- Hero Section -->
<section class="hero">
  <h1>Bienvenue sur mon Portfolio</h1>
</section>

<!-- Annonce après le hero -->
<div class="container mx-auto my-8 px-4">
  <AdSense 
    client="ca-pub-VOTRE_ID"
    slot="1111111111"
  />
</div>

<!-- Vos autres sections -->
```

---

### 3. Dans les articles de blog individuels

Si vous créez des pages pour chaque article :

```svelte
<!-- src/routes/blog/[slug]/+page.svelte -->
<script>
  import AdSense from '$lib/components/AdSense.svelte';
  export let data; // Vos données d'article
</script>

<article class="max-w-4xl mx-auto px-4 py-12">
  <h1>{data.title}</h1>
  
  <!-- Annonce après le titre -->
  <div class="my-8">
    <AdSense client="ca-pub-VOTRE_ID" slot="2222222222" />
  </div>
  
  <!-- Contenu de l'article -->
  <div class="prose">
    {@html data.content}
  </div>
  
  <!-- Annonce avant le footer -->
  <div class="my-8">
    <AdSense client="ca-pub-VOTRE_ID" slot="3333333333" format="horizontal" />
  </div>
</article>
```

---

### 4. Layout global avec AdSense dans le Sidebar

```svelte
<!-- src/routes/+layout.svelte -->
<script>
  import AdSense from '$lib/components/AdSense.svelte';
</script>

<div class="flex">
  <!-- Contenu principal -->
  <main class="flex-1">
    <slot />
  </main>
  
  <!-- Sidebar avec annonce -->
  <aside class="w-80 p-4 hidden lg:block">
    <div class="sticky top-4">
      <h3 class="font-bold mb-4">Publicité</h3>
      <AdSense 
        client="ca-pub-VOTRE_ID"
        slot="4444444444"
        format="vertical"
        style="display:block; height: 600px;"
      />
    </div>
  </aside>
</div>
```

---

## 🎨 Formats d'annonces recommandés

### Horizontal (Leaderboard)
```svelte
<AdSense 
  client="ca-pub-XXX"
  slot="XXX"
  format="horizontal"
  style="display:block; text-align:center;"
/>
```
**Utilisation** : En haut de page, entre sections

---

### Rectangle (Medium Rectangle)
```svelte
<AdSense 
  client="ca-pub-XXX"
  slot="XXX"
  format="rectangle"
  style="display:inline-block; width:300px; height:250px;"
/>
```
**Utilisation** : Dans le contenu, sidebar

---

### Vertical (Skyscraper)
```svelte
<AdSense 
  client="ca-pub-XXX"
  slot="XXX"
  format="vertical"
  style="display:inline-block; width:160px; height:600px;"
/>
```
**Utilisation** : Sidebar fixe

---

### Responsive (Auto-adaptatif)
```svelte
<AdSense 
  client="ca-pub-XXX"
  slot="XXX"
  format="auto"
  responsive={true}
  style="display:block;"
/>
```
**Utilisation** : Partout (s'adapte automatiquement)

---

## 📊 Positionnement optimal pour maximiser les revenus

### Layout type "Blog"
```
┌─────────────────────────────┐
│         HEADER              │
├─────────────────────────────┤
│      HERO SECTION           │
├─────────────────────────────┤
│    [ANNONCE HORIZONTAL]     │ ← RPM élevé
├─────────────────────────────┤
│                             │
│   ARTICLE 1  ARTICLE 2      │
│                             │
│   ARTICLE 3  ARTICLE 4      │
│                             │
├─────────────────────────────┤
│    [ANNONCE RESPONSIVE]     │ ← RPM moyen
├─────────────────────────────┤
│   ARTICLE 5  ARTICLE 6      │
│                             │
└─────────────────────────────┘
```

### Layout type "Portfolio"
```
┌──────────────────┬─────────┐
│     CONTENT      │ SIDEBAR │
│                  │         │
│  Hero            │ [AD]    │
│  About           │ [AD]    │
│  Projects        │ [AD]    │
│                  │         │
│  [ANNONCE]       │         │
│                  │         │
│  Skills          │         │
│  Contact         │         │
└──────────────────┴─────────┘
```

---

## ⚠️ Bonnes pratiques IMPORTANTES

### ✅ À FAIRE
- Utiliser 1-3 annonces par page
- Laisser de l'espace autour des annonces
- Utiliser des formats responsive
- Tester sur mobile et desktop
- Attendre 24-48h après intégration

### ❌ À NE PAS FAIRE
- Ne pas mettre trop d'annonces (> 4-5)
- Ne jamais cliquer sur vos propres annonces
- Ne pas cacher ou modifier les annonces
- Ne pas forcer les clics
- Ne pas mettre d'annonces sur pages vides

---

## 🔧 Dépannage courant

### Problème : Les annonces ne s'affichent pas
**Solutions :**
1. Vérifier que votre compte AdSense est approuvé
2. Attendre 24-48h après l'intégration
3. Désactiver AdBlock pour tester
4. Vérifier la console (F12) pour les erreurs
5. Vérifier que les IDs (client & slot) sont corrects

### Problème : Espace vide à la place de l'annonce
**Raison :** Normal si :
- Pas assez de trafic
- AdBlocker activé
- Pas d'annonceurs pour votre niche
- Compte pas encore approuvé

### Problème : Revenus très faibles
**Solutions :**
- Augmenter le trafic (SEO, social media)
- Créer plus de contenu de qualité
- Cibler des niches rentables (tech, finance)
- Optimiser le placement des annonces
- Améliorer le temps de visite des utilisateurs

---

## 📈 Tracker les performances

### Variables d'environnement pour tester
```
# .env
PUBLIC_ADSENSE_CLIENT=ca-pub-VOTRE_ID
PUBLIC_ADSENSE_ENABLED=true
```

### Composant avec analytics
```svelte
<script>
  import AdSense from '$lib/components/AdSense.svelte';
  import { browser } from '$app/environment';
  
  function trackAdView() {
    if (browser && window.gtag) {
      window.gtag('event', 'ad_view', {
        'event_category': 'adsense',
        'event_label': 'blog_top'
      });
    }
  }
</script>

<div on:mouseenter={trackAdView}>
  <AdSense client="..." slot="..." />
</div>
```

---

## ✅ Checklist d'intégration

- [ ] Composant AdSense créé
- [ ] Compte AdSense approuvé (peut prendre 1-2 semaines)
- [ ] Publisher ID obtenu (ca-pub-XXX)
- [ ] Unités publicitaires créées sur AdSense Dashboard
- [ ] Slots ID obtenus pour chaque unité
- [ ] Code intégré dans 2-3 pages stratégiques
- [ ] Test sur desktop et mobile
- [ ] Attendre 24-48h pour voir les premières annonces
- [ ] Monitorer les performances dans AdSense Dashboard

---

**Bon courage avec la monétisation ! 💰**

