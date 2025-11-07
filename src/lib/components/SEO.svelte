<script lang="ts">
  export let title = 'El Houcine QARA - Full Stack Developer';
  export let description = 'Full Stack Developer specializing in Laravel, React, Svelte, Node.js. Building scalable web applications with modern technologies. 2+ years experience in enterprise solutions.';
  export let keywords = 'Full Stack Developer, Web Developer, Laravel Developer, React Developer, Node.js, Svelte, TypeScript, Morocco Developer, Software Engineer, Web Applications';
  export let author = 'El Houcine QARA';
  export let image = 'https://your-domain.com/images/og-image.jpg';
  export let url = 'https://your-domain.com';
  export let type = 'website';
</script>

<svelte:head>
  <!-- Primary Meta Tags -->
  <title>{title}</title>
  <meta name="title" content={title} />
  <meta name="description" content={description} />
  <meta name="keywords" content={keywords} />
  <meta name="author" content={author} />
  <meta name="robots" content="index, follow" />
  <meta name="language" content="English" />
  <meta name="revisit-after" content="7 days" />
  
  <!-- Open Graph / Facebook -->
  <meta property="og:type" content={type} />
  <meta property="og:url" content={url} />
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:image" content={image} />
  <meta property="og:site_name" content="El Houcine QARA Portfolio" />
  
  <!-- Twitter -->
  <meta property="twitter:card" content="summary_large_image" />
  <meta property="twitter:url" content={url} />
  <meta property="twitter:title" content={title} />
  <meta property="twitter:description" content={description} />
  <meta property="twitter:image" content={image} />
  <meta property="twitter:creator" content="@yourhandle" />
  
  <!-- Additional SEO -->
  <link rel="canonical" href={url} />
  
  <!-- Structured Data -->
  <script type="application/ld+json">
    {JSON.stringify({
      "@context": "https://schema.org",
      "@type": "Person",
      "name": "El Houcine QARA",
      "url": url,
      "image": image,
      "jobTitle": "Full Stack Developer",
      "description": description,
      "alumniOf": "ENSET Mohammedia",
      "knowsAbout": [
        "Laravel",
        "React",
        "Svelte",
        "Node.js",
        "TypeScript",
        "Full Stack Development",
        "Web Development",
        "Software Engineering"
      ],
      "sameAs": [
        "https://www.linkedin.com/in/el-houcine-qara-927b07302/",
        "https://github.com/elhoucineqara",
        "https://wa.me/212637446431"
      ]
    })}
  </script>
</svelte:head>

