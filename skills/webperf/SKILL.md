---
name: webperf
description: Audit and improve web performance with actual measurements, not guesses. Use when a change could affect page load, rendering, or runtime performance, or when the user asks about speed/performance of a web app.
---

# /webperf

Measure before you optimize. The goal is to find the real bottleneck with data,
fix that specific thing, then measure again — not to guess and add caching
everywhere.

## Steps

1. **Measure first.** Use whatever's available: browser DevTools Performance/Network tabs, Lighthouse, `webpack-bundle-analyzer` or equivalent, actual timing logs. Don't optimize based on assumption.
2. **Identify the specific bottleneck**, e.g.:
   - Large JS bundle → check for unnecessary dependencies, missing code-splitting
   - Slow initial render → check for render-blocking resources, unoptimized images, missing lazy-loading
   - Slow API calls → check for N+1 queries, missing indexes, unnecessary payload size
   - Layout shift → check for images/embeds without reserved dimensions
3. **Fix the specific thing that measurement pointed at.** Apply `minimal-implementation` here too — the fix for a 2MB image is compressing it, not adding a CDN.
4. **Re-measure after the fix** to confirm it actually helped, using the same method as the baseline measurement.
5. **Report before/after numbers**, not just "should be faster now."

## Common checks

- Bundle size and what's in it (unused dependencies, duplicate packages)
- Render-blocking CSS/JS
- Image sizes and formats (compressed, correctly sized, modern formats where supported)
- Unnecessary re-renders (React/Vue-style frameworks)
- Network waterfall (sequential requests that could be parallel or cached)

## Output

Baseline measurement → change made → new measurement, in that order, so the
improvement is demonstrated rather than asserted.
