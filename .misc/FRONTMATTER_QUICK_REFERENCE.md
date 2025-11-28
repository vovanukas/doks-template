# Doks Frontmatter Quick Reference

## 📝 Blog Post Template

```yaml
---
title: "Your Blog Post Title"
description: "SEO description"
summary: "Summary for blog cards"
date: 2024-01-15T10:00:00-05:00
lastmod: 2024-01-15T10:00:00-05:00
draft: false
weight: 50
categories: ["Category1", "Category2"]
tags: ["tag1", "tag2", "tag3"]
contributors: ["Author Name"]
pinned: false
homepage: false
seo:
  title: ""
  description: ""
  canonical: ""
  noindex: false
---
```

## 📚 Documentation Page Template

```yaml
---
title: "Documentation Page Title"
description: "SEO description"
summary: ""
date: 2024-01-15T10:00:00-05:00
lastmod: 2024-01-15T10:00:00-05:00
draft: false
weight: 999
toc: true
seo:
  title: ""
  description: ""
  canonical: ""
  noindex: false
---
```

## 📁 Section Index (_index.md) Template

```yaml
---
title: "Section Name"
description: "Section description"
summary: ""
date: 2024-01-15T10:00:00-05:00
lastmod: 2024-01-15T10:00:00-05:00
draft: false
weight: 50
---
```

## 🎯 Field Purpose Cheat Sheet

| Field | Used For | Example |
|-------|----------|---------|
| `title` | Page title (shown in header & nav) | "Getting Started Guide" |
| `description` | SEO & meta tags | "Learn how to..." |
| `summary` | Card previews & lists | "This guide covers..." |
| `lead` | Intro paragraph below title | "Welcome to our docs!" |
| `weight` | Navigation order (lower = first) | `100` |
| `toc` | Show/hide table of contents | `true` |
| `draft` | Hide from production | `false` |
| `date` | Publication date | `2024-01-15T10:00:00Z` |
| `lastmod` | Last update date | `2024-01-15T10:00:00Z` |
| `categories` | Blog post categories | `["News", "Updates"]` |
| `tags` | Blog post tags | `["tutorial", "beginner"]` |
| `contributors` | Blog post authors | `["John Doe"]` |
| `pinned` | Pin to top of blog | `true` |
| `homepage` | Show on homepage | `true` |
| `exclude_search` | Hide from search | `false` |
| `sitemap_exclude` | Hide from sitemap | `false` |

## 🔍 SEO Object Fields

```yaml
seo:
  title: "Custom SEO Title"           # Override page title for SEO
  description: "Meta description"     # 150-160 chars recommended
  canonical: "https://example.com/"   # Canonical URL
  noindex: false                      # Prevent search indexing
```

## 🎨 Content Type Differences

### Blog Posts Need:
- ✅ `categories` - Organize posts
- ✅ `tags` - Tag posts
- ✅ `contributors` - Author names
- ✅ `date` - Required for sorting
- ✅ `pinned` - Pin important posts
- ✅ `homepage` - Feature on homepage

### Documentation Needs:
- ✅ `weight` - Navigation order
- ✅ `toc` - Table of contents
- ✅ `lead` - Intro paragraph
- ❌ No categories/tags needed

### Section Indexes (_index.md):
- ✅ `title` - Section name
- ✅ `weight` - Section order
- ❌ Usually no TOC needed

## 📊 Weight Guidelines

| Content Type | Typical Weight | Purpose |
|--------------|---------------|---------|
| Important pages | 1-99 | Appear first |
| Normal pages | 100-899 | Standard order |
| Low priority | 900-999 | Appear last |

**Lower weight = Higher in navigation**

## 🎯 Common Use Cases

### Pin a Blog Post to Top
```yaml
pinned: true
weight: 1
```

### Feature Post on Homepage
```yaml
homepage: true
pinned: true
```

### Hide Page from Search
```yaml
exclude_search: true
seo:
  noindex: true
```

### Redirect Old URLs
```yaml
aliases:
  - /old-url/
  - /another-old-url/
```

### Documentation Navigation Order
```yaml
# First page in section
weight: 100

# Second page
weight: 200

# Last page
weight: 999
```

## 📅 Date Format

Always use ISO 8601 format:
```yaml
date: 2024-01-15T10:00:00-05:00
#     YYYY-MM-DDTHH:MM:SS+TZ
```

Or use UTC:
```yaml
date: 2024-01-15T15:00:00Z
```

## 🖼️ Featured Images

For blog posts with featured images, add image to page bundle:

```
content/
  blog/
    my-post/
      index.md          ← Blog post
      feature.jpg       ← Featured image (auto-detected)
```

Name patterns that work:
- `feature.*`
- `cover.*`
- `thumbnail.*`

## 👥 Contributors Setup

1. Create contributor taxonomy:
```
content/contributors/john-doe/_index.md
```

2. Add avatar to contributor page:
```yaml
---
title: "John Doe"
avatar: "avatar.jpg"  # In same directory
---
```

3. Reference in blog post:
```yaml
contributors: ["John Doe"]
```

## ⚡ Performance Tips

- Use `exclude_search: true` for large pages you don't want indexed
- Use `sitemap_exclude: true` for private/internal pages
- Keep descriptions under 160 characters
- Use `toc: false` for short pages (improves layout)

## 🚫 Common Mistakes

❌ **Don't do this:**
```yaml
title:              # Empty title (required!)
weight: abc         # Must be number
date: 2024-01-15    # Missing time
tags: tag1, tag2    # Must be array
```

✅ **Do this:**
```yaml
title: "My Title"
weight: 100
date: 2024-01-15T10:00:00Z
tags: ["tag1", "tag2"]
```

## 📦 Schema Files Available

| File | Use For |
|------|---------|
| `frontmatter-blog-jsonSchema.json` | Blog posts |
| `frontmatter-blog-uiSchema.json` | Blog UI config |
| `frontmatter-docs-jsonSchema.json` | Documentation |
| `frontmatter-docs-uiSchema.json` | Docs UI config |
| `frontmatter-jsonSchema.json` | All content types |
| `frontmatter-uiSchema.json` | General UI config |

## 🔗 Resources

- [Full Documentation](./FRONTMATTER_SCHEMAS_README.md)
- [Doks Theme Docs](https://getdoks.org/)
- [Hugo Front Matter](https://gohugo.io/content-management/front-matter/)
- [RJSF Documentation](https://rjsf-team.github.io/react-jsonschema-form/)

---

**Pro Tip:** Open `frontmatter-editor-example.html` in your browser for a visual form editor! 🎨



