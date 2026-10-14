YOUR WEB CREATORS
Complete static agency website — October 14, 2026

WHAT IS INCLUDED
22 complete HTML pages, one shared CSS file, one shared JavaScript file,
37 local JPEG photographs, one SVG favicon, one local MP4, and .htaccess.
The ZIP extracts directly into the requested file tree, with no parent wrapper.
No build step, package installation, framework, or application server is needed.

QUICK START: APACHE / XAMPP / CPANEL
1. Extract the complete ZIP. Keep .htaccess; it is hidden on some systems.
2. Put the contents in your domain's Apache document root (often public_html).
3. Enable Apache mod_rewrite and allow this directory's .htaccess directives.
   Apache 2.4+ is required because the rewrite rules use the END flag.
4. Open the site's domain. Use /services, /work, /services/seo, and /pricing.

For a local machine, XAMPP with Apache is a straightforward option:
- Extract into C:/xampp/htdocs/ywc (Windows) or an equivalent folder.
- In Apache's httpd-vhosts.conf, add the following virtual host, adjusting only
  the path if your extraction directory differs:

<VirtualHost *:80>
    ServerName ywc.test
    DocumentRoot "C:/xampp/htdocs/ywc"
    <Directory "C:/xampp/htdocs/ywc">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

- Ensure httpd.conf includes conf/extra/httpd-vhosts.conf and loads rewrite_module.
- Add "127.0.0.1 ywc.test" to your operating system's hosts file.
  On Windows: C:/Windows/System32/drivers/etc/hosts (administrator access needed).
- Restart Apache and open http://ywc.test/.

A file:// double-click or plain python -m http.server does NOT process .htaccess.
Use Apache for the intended clean URLs and custom 404 behavior. This is a static
site; Apache is only serving files and applying URL rules, not running a backend.

SUBFOLDER INSTALLATION
Most links and asset paths are relative, so the regular pages support a subfolder.
If you install at https://example.com/ywc/ instead of a domain root:
1. In .htaccess, change RewriteBase / to RewriteBase /ywc/.
2. Change ErrorDocument 404 /404 to ErrorDocument 404 /ywc/404.
3. In 404.html, change the ywc-root meta content from / to /ywc/ and prepend
   /ywc to root-relative href="/…" and src="/…" attributes. This exception keeps
   the error page's assets working even for deeply nested missing URLs. Do not
   alter absolute https:// URLs or hash-only links.
4. Update canonical and Open Graph URLs to your actual deployment URL.

CLEAN URL DETAILS
- /services.html redirects to /services; nested .html addresses do the same.
- /index.html and /index redirect to the home route.
- Existing extensionless page requests internally resolve to their .html files.
- /services, /work, and /blog resolve to listing pages before same-named folders.
- The three listing directory forms with trailing / redirect to the clean route.
- Query strings are retained for the project and article variations.
- Missing paths receive a real HTTP 404 and the branded error page.
- Options -MultiViews prevents content-negotiation conflicts.
- DirectorySlash Off prevents same-named directories from hijacking listing pages.
- Options -Indexes prevents folder listings.
- If you receive a server 500, read the Apache error log. Shared hosts may restrict
  Options, DirectorySlash, or AllowOverride. Ask the host to allow these rules,
  or put equivalent directives in the virtual-host configuration.
- Nginx and non-Apache static hosts ignore .htaccess and need equivalent routing.

FILE MAP
index.html                         Complete 12-part home experience including footer
services.html                      All ten services
work.html                          Six filterable concept studies
about.html                         Agency story, values, and team disciplines
pricing.html                       Two payment columns, calculator, detailed scopes
contact.html                       Inquiry form, email, and social sharing links
blog.html                          Six searchable original articles
404.html                           Custom error page
privacy-policy.html                Privacy policy for this static/no-tracking build
terms-and-conditions.html          Website terms and service-contract principles
services/logo-design.html
services/branding-solutions.html
services/web-design-development.html
services/ecommerce-development.html
services/digital-marketing.html
services/seo.html
services/ppc-sem.html
services/mobile-app-development.html
services/video-editing-animation.html
services/domain-hosting.html
work/project-template.html         Complete reusable case study with six variations
blog/post-template.html            Complete reusable article with six full articles
assets/css/style.css               Libraries, embedded fonts, custom design system
assets/js/script.js                Libraries, article/case data, vanilla site behavior
assets/images/                     All photographs plus favicon.svg
assets/videos/hero.mp4              Local hero background video
.htaccess                          Apache clean URLs, 404, basic headers/compression
README.txt                         This guide, source URLs, and license notices

EDITING THE WEBSITE
All primary page content is in HTML inside <main>. It is not injected by a
header/footer component. The header and footer are repeated intentionally so
all 22 pages remain navigable without JavaScript. Update shared navigation,
logo markup, or footer text consistently across all pages.

The custom CSS begins at the YOUR WEB CREATORS / Custom design system banner.
The custom behavior begins at YOUR WEB CREATORS / Site behavior. Vendor code is
bundled first to preserve the exact requested one-CSS/one-JS structure. Keep
license headers. There is no source-map dependency and no remote font request.

Reusable case studies use work/project-template?project=forma (or northstar,
fieldwork, verve, goodwell, relay). Articles use blog/post-template?post=homepage-job
(or brand-before-logo, checkout-friction, seo-basics, better-brief,
motion-with-purpose). The complete first case and first article also exist in
static HTML. Other query variations are enhanced by JavaScript. Their title,
description, and canonical URL update client-side. For production SEO/social
crawlers that do not execute JavaScript, duplicate the template into separate
static pages with each variation's copy and metadata, then update listing links.
No unknown query value is injected into the page; unknown IDs show the default.

The variation data is in window.YWC_CONTENT in assets/js/script.js, immediately
before the site-behavior banner. To reuse the layouts, edit this data as well as
the initial static HTML. Each article includes five complete original sections.

IMAGES, VIDEO, AND LOGOS
All media is local and replaceable. No AI images are included.
- hero-poster.jpg: preview frame for the background video.
- hero.mp4: 9-second muted purple-liquid stock video (1600x900, H.264, 24fps).
  Replace it in assets/videos and replace the poster to match. Keep video small,
  muted, and broadly compatible. The site pauses it for reduced motion and when
  it is outside the visible area.
- project-01.jpg through project-06.jpg: six portfolio concept photographs.
- service-01.jpg through service-10.jpg: service previews and service hero images.
- blog-01.jpg through blog-06.jpg: editorial article images.
- testimonial-01.jpg through testimonial-10.jpg: stock portrait imagery.
- team-01.jpg through team-03.jpg: photographs illustrating team disciplines.
- studio.jpg: the about section and about-page photograph.
- favicon.svg: standalone version of the geometric brandmark.

Recommended replacements: project/service/blog images at least 1400px wide,
portraits at least 256x256, studio images at least 1600px wide. Use the current
filenames to avoid changing paths. Preserve sensible file sizes and update alt
text to accurately describe replacement media. CSS object-fit controls cropping.

The inline SVG with class="brandmark" is repeated in headers and footers. The
same prism geometry is used in favicon.svg. Edit both for a logo replacement.
The marquee symbols are generic geometric icons, not real client logos.
Bricolage Grotesque and Manrope variable fonts and Instrument Serif italic are
embedded as WOFF2 data in style.css. Their SIL Open Font License notices follow.

THEME AND ACCESSIBILITY
- Light is the initial theme; the bottom-right moon/sun toggle works on each page.
- localStorage key ywc-theme stores light/dark. Storage failures are non-fatal.
- Theme selection is applied in the head before styling to reduce color flash.
- ywc-motion stores the visitor's motion preference. Reduced motion takes priority.
- Pause motion controls stop continuous decoration and smooth scrolling.
- SplitText word reveals are applied only after fonts settle, without hiding
  the page while fonts or JavaScript load.
- IntersectionObserver triggers section reveals. No ScrollTrigger is loaded.
- Three GSAP marquees run right-to-left, left-to-right, right-to-left. No CSS
  marquee keyframes or deprecated marquee elements are used.
- GSAP quickTo moves the decorative desktop service preview. Touch and keyboard
  visitors retain the same service links and descriptions without that effect.
- Swiper is used only for the ten-review carousel and does not auto-advance.
- Native details/summary FAQs work with a keyboard and without JavaScript.
- Content remains readable if an animation dependency is unavailable.

CONTACT FORM AND IDENTITY
There is no backend, database, payment integration, or email delivery service.
The form validates required fields in the browser and prepares a mailto draft.
The visitor must open and send that email, or copy the brief into an email app.
Nothing is represented as sent before the visitor sends it. Longer briefs have
a copy option because email-client URL limits vary.

The branded default mailbox is hello@yourwebcreators.com, and the canonical
site domain is https://yourwebcreators.com. Verify that you own this exact domain
and that the mailbox receives mail before publication. Change these values in
all HTML files and in script.js if needed. Delivery to this mailbox was not tested.

No verified company social-profile URLs were provided. LinkedIn and X icons are
working social SHARE links, not invented profile pages. Replace their href values
with verified company profiles if you want profile links instead, and update
the adjacent labels/accessible names to match their purpose.

PORTFOLIO, TEAM, AND TESTIMONIAL CONTENT
The six portfolio entries are complete, clearly identified independent concept
studies, not fabricated client engagements or performance claims. Team sections
present working disciplines and stock workspace photos rather than invented staff.

The ten review cards have distinct original quotes, names, and stock portraits.
They are explicitly marked illustrative because no verified customer reviews were
supplied. Do not present them as authentic endorsements. Replace each quote,
attribution, and portrait with an approved real client review before removing the
illustrative disclosure. This is the deliberate exception to the request to show
fictional testimonials without labeling them.

PRICING MODEL
The figures are proposed starting packages, subject to a written scope:
Monthly Rental = upfront price x 1.25 / 12.
Rental total = upfront price x 1.25.
Upfront saving = 20% of the rental total (not 25% of that total).
Example: website upfront $2,880; monthly $300 x 12 = $3,600; saving $720.
Marketing, SEO, PPC, and hosting are defined 12-month services. Other packages
cover a specified project. Taxes, ad spend, domains, platform fees, and third-party
licenses are separate. The pages describe the 12-month commitment and ownership
conditions; there is no misleading cancel-anytime promise or automatic checkout.

LEGAL CONTENT
The privacy and terms pages are complete original drafting baselines tailored to
this no-tracking, browser-email-draft implementation. They do not invent an entity
registration, street address, governing state, regulatory status, or attorney review.
Before launch, a qualified attorney should confirm them against the actual legal
entity, contracts, jurisdiction, vendors, retention practices, and applicable law.
Update the privacy page before adding form submission, analytics, advertising
pixels, newsletter tools, or other collection. A generic draft cannot guarantee
legal compliance for an unseen operating business.

Primary references checked while drafting:
https://oag.ca.gov/privacy/business-privacy
https://oag.ca.gov/privacy/ccpa
https://gsap.com/docs/v3/Installation/

VERIFICATION
- 22 complete documents; every page includes a substantive <main>.
- Native HTML/link/media/ID checks across the requested tree.
- JavaScript syntax checked with Node.
- 95 DOM/interaction assertions cover theme persistence, reduced motion, mobile
  menu disclosure, work filtering, article search and reset, all six case variants,
  all six article variants, subfolder URL resolution, all ten pricing comparisons,
  form prefill/draft/copy behavior, and invalidation of a draft after edits.
- All local JPEGs decode, and the MP4 is H.264 with a valid duration and dimensions.
- ZIP membership and CRC integrity verified before delivery.
- No browser layout engine was available in the execution environment. Responsive
  layouts and animations have not received browser visual QA, and .htaccess has
  not been executed against a live Apache instance. Test desktop/mobile layouts,
  animation timing, direct clean URLs, nested unknown URLs, and email-client draft
  behavior in your own Apache environment before public launch.

PINNED DEPENDENCIES
GSAP 3.15.0 with SplitText 3.15.0 and TextPlugin 3.15.0 only.
Lenis 1.3.17. Swiper 11.2.10. Bootstrap Grid 5.3.8 (grid/layout/spacing only).
No Bootstrap component JS/CSS, jQuery, frameworks, page builder, Hover.css,
ScrollTrigger, or other separately loaded GSAP plugins.

ASSET SOURCES AND THIRD-PARTY LICENSE NOTICES
The following record includes original sources and license notices. Preserve it
when distributing the bundled third-party libraries and fonts. Stock images and
video are replaceable imagery, not evidence of client relationships.

YWC ASSET SOURCES / DEPENDENCY VERSIONS
Fetched 2026-10-14. Assets are local placeholders, not evidence of a client engagement.
All photographs are downloaded from images.unsplash.com; swap with approved project/team/client photographs before publication.
No AI image generation was used.

VENDOR DEPENDENCIES
gsap.min.js
https://cdn.jsdelivr.net/npm/gsap@3.15.0/dist/gsap.min.js
SplitText.min.js
https://cdn.jsdelivr.net/npm/gsap@3.15.0/dist/SplitText.min.js
TextPlugin.min.js
https://cdn.jsdelivr.net/npm/gsap@3.15.0/dist/TextPlugin.min.js
lenis.min.js
https://cdn.jsdelivr.net/npm/lenis@1.3.17/dist/lenis.min.js
lenis.css
https://cdn.jsdelivr.net/npm/lenis@1.3.17/dist/lenis.css
swiper-bundle.min.js
https://cdn.jsdelivr.net/npm/swiper@11.2.10/swiper-bundle.min.js
swiper-bundle.min.css
https://cdn.jsdelivr.net/npm/swiper@11.2.10/swiper-bundle.min.css
bootstrap-grid.min.css
https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap-grid.min.css

FONTS (embedded WOFF2, Latin subset)
Bricolage Grotesque
https://fonts.gstatic.com/s/bricolagegrotesque/v9/3y9K6as8bTXq_nANBjzKo3IeZx8z6up5BeSl9D4dj_x9PpZBMlGIInE.woff2
Instrument Serif
https://fonts.gstatic.com/s/instrumentserif/v5/jizHRFtNs2ka5fXjeivQ4LroWlx-6zAjjH7M.woff2
Manrope
https://fonts.gstatic.com/s/manrope/v20/xn7gYHE41ni1AdIRggexSg.woff2
Google Fonts CSS source: https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,200..800&family=Instrument+Serif:ital@1&family=Manrope:wght@200..800&display=swap

PHOTOGRAPHS
blog-01.jpg — Reused stock image for article card
Copied from project-01.jpg
blog-02.jpg — Reused stock image for article card
https://images.unsplash.com/photo-1608571423902-eed4a5ad8108?auto=format&fit=crop&w=1400&h=1050&q=82&fm=jpg
blog-03.jpg — Reused stock image for article card
Copied from project-03.jpg
blog-04.jpg — Reused stock image for article card
https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?auto=format&fit=crop&w=1200&h=900&q=82&fm=jpg
blog-05.jpg — Reused stock image for article card
Copied from project-05.jpg
blog-06.jpg — Reused stock image for article card
Copied from project-06.jpg
project-01.jpg — Modern architectural interior
https://images.unsplash.com/photo-1600607687920-4e2a09cf159d?auto=format&fit=crop&w=1400&h=1050&q=82&fm=jpg
project-02.jpg — Abstract digital waves for the Northstar software concept
https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=1400&h=1050&q=82&fm=jpg
project-03.jpg — Contemporary workspace
https://images.unsplash.com/photo-1497366754035-f200968a6e72?auto=format&fit=crop&w=1200&h=900&q=82&fm=jpg
project-04.jpg — Warm restaurant interior for the Verve hospitality concept
https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?auto=format&fit=crop&w=1200&h=900&q=82&fm=jpg
project-05.jpg — Commerce and payment
https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?auto=format&fit=crop&w=1200&h=900&q=82&fm=jpg
project-06.jpg — Architectural perspective
https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?auto=format&fit=crop&w=1600&h=800&q=82&fm=jpg
service-01.jpg — Abstract visual texture
https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-02.jpg — Graphic design tools and color samples
https://images.unsplash.com/photo-1558655146-9f40138edfeb?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-03.jpg — Website planning workstation
https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-04.jpg — Ecommerce payment
https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-05.jpg — Digital marketing analytics
https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-06.jpg — Search and measurement
https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-07.jpg — Campaign strategy
https://images.unsplash.com/photo-1553877522-43269d4ea984?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-08.jpg — Mobile phone application
https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-09.jpg — Video production
https://images.unsplash.com/photo-1574717024653-61fd2cf4d44d?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
service-10.jpg — Server hardware
https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&w=800&h=600&q=82&fm=jpg
studio.jpg — Creative office interior
https://images.unsplash.com/photo-1524758631624-e2822e304c36?auto=format&fit=crop&w=1400&h=1000&q=82&fm=jpg
team-01.jpg — Stock collaboration photograph
https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&w=800&h=1000&q=82&fm=jpg
team-02.jpg — Stock strategy photograph
https://images.unsplash.com/photo-1553877522-43269d4ea984?auto=format&fit=crop&w=800&h=1000&q=82&fm=jpg
team-03.jpg — Stock creative meeting photograph
https://images.unsplash.com/photo-1556761175-b413da4baf72?auto=format&fit=crop&w=800&h=1000&q=82&fm=jpg
testimonial-01.jpg — Stock portrait 1
https://images.unsplash.com/photo-1438761681033-6461ffad8d80?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-02.jpg — Stock portrait 2
https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-03.jpg — Stock portrait 3
https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-04.jpg — Stock portrait 4
https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-05.jpg — Stock portrait 5
https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-06.jpg — Stock portrait 6
https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-07.jpg — Stock portrait 7
https://images.unsplash.com/photo-1488426862026-3ee34a7d66df?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-08.jpg — Stock portrait 8
https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-09.jpg — Stock portrait 9
https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=240&h=240&q=82&fm=jpg
testimonial-10.jpg — Stock portrait 10
https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?auto=format&fit=crop&crop=faces&w=240&h=240&q=82&fm=jpg

HERO VIDEO / POSTER
Hero source page: https://coverr.co/videos/purple-liquid-xbisxxl39w
Original MP4: https://cdn.coverr.co/videos/coverr-purple-liquid-6048/1080p.mp4
hero.mp4: first 9 seconds, resized to 1600×900, 24fps, H.264, no audio, faststart.
hero-poster.jpg: frame from the original clip at 3 seconds.
Coverr license: https://coverr.co/license
Unsplash license: https://unsplash.com/license

THIRD-PARTY NOTICES
The original library license banners are retained in downloaded sources. Full MIT/OFL notices below must be included in the delivered README.txt when concatenating vendor files.

--- LENIS-LICENSE.txt ---
The MIT License

Copyright (c) 2024 darkroom.engineering

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

--- SWIPER-LICENSE.txt ---
The MIT License (MIT)

Copyright (c) 2019 Vladimir Kharlampidi

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


--- BOOTSTRAP-LICENSE.txt ---
The MIT License (MIT)

Copyright (c) 2011-2025 The Bootstrap Authors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.


--- BRICOLAGE-GROTESQUE-OFL.txt ---
Copyright 2022 The Bricolage Grotesque Project Authors (https://github.com/ateliertriay/bricolage)

This Font Software is licensed under the SIL Open Font License, Version 1.1.
This license is copied below, and is also available with a FAQ at:
https://scripts.sil.org/OFL


-----------------------------------------------------------
SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded, 
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.


--- MANROPE-OFL.txt ---
Copyright 2018 The Manrope Project Authors (https://github.com/googlefonts/manrope)

This Font Software is licensed under the SIL Open Font License, Version 1.1.
This license is copied below, and is also available with a FAQ at:
http://scripts.sil.org/OFL


-----------------------------------------------------------
SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded, 
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.


--- INSTRUMENT-SERIF-OFL.txt ---
Copyright 2022 The Instrument Serif Project Authors (https://github.com/Instrument/instrument-serif)

This Font Software is licensed under the SIL Open Font License, Version 1.1.
This license is copied below, and is also available with a FAQ at:
https://scripts.sil.org/OFL


-----------------------------------------------------------
SIL OPEN FONT LICENSE Version 1.1 - 26 February 2007
-----------------------------------------------------------

PREAMBLE
The goals of the Open Font License (OFL) are to stimulate worldwide
development of collaborative font projects, to support the font creation
efforts of academic and linguistic communities, and to provide a free and
open framework in which fonts may be shared and improved in partnership
with others.

The OFL allows the licensed fonts to be used, studied, modified and
redistributed freely as long as they are not sold by themselves. The
fonts, including any derivative works, can be bundled, embedded, 
redistributed and/or sold with any software provided that any reserved
names are not used by derivative works. The fonts and derivatives,
however, cannot be released under any other type of license. The
requirement for fonts to remain under this license does not apply
to any document created using the fonts or their derivatives.

DEFINITIONS
"Font Software" refers to the set of files released by the Copyright
Holder(s) under this license and clearly marked as such. This may
include source files, build scripts and documentation.

"Reserved Font Name" refers to any names specified as such after the
copyright statement(s).

"Original Version" refers to the collection of Font Software components as
distributed by the Copyright Holder(s).

"Modified Version" refers to any derivative made by adding to, deleting,
or substituting -- in part or in whole -- any of the components of the
Original Version, by changing formats or by porting the Font Software to a
new environment.

"Author" refers to any designer, engineer, programmer, technical
writer or other person who contributed to the Font Software.

PERMISSION & CONDITIONS
Permission is hereby granted, free of charge, to any person obtaining
a copy of the Font Software, to use, study, copy, merge, embed, modify,
redistribute, and sell modified and unmodified copies of the Font
Software, subject to the following conditions:

1) Neither the Font Software nor any of its individual components,
in Original or Modified Versions, may be sold by itself.

2) Original or Modified Versions of the Font Software may be bundled,
redistributed and/or sold with any software, provided that each copy
contains the above copyright notice and this license. These can be
included either as stand-alone text files, human-readable headers or
in the appropriate machine-readable metadata fields within text or
binary files as long as those fields can be easily viewed by the user.

3) No Modified Version of the Font Software may use the Reserved Font
Name(s) unless explicit written permission is granted by the corresponding
Copyright Holder. This restriction only applies to the primary font name as
presented to the users.

4) The name(s) of the Copyright Holder(s) or the Author(s) of the Font
Software shall not be used to promote, endorse or advertise any
Modified Version, except to acknowledge the contribution(s) of the
Copyright Holder(s) and the Author(s) or with their explicit written
permission.

5) The Font Software, modified or unmodified, in part or in whole,
must be distributed entirely under this license, and must not be
distributed under any other license. The requirement for fonts to
remain under this license does not apply to any document created
using the Font Software.

TERMINATION
This license becomes null and void if any of the above conditions are
not met.

DISCLAIMER
THE FONT SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT
OF COPYRIGHT, PATENT, TRADEMARK, OR OTHER RIGHT. IN NO EVENT SHALL THE
COPYRIGHT HOLDER BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
INCLUDING ANY GENERAL, SPECIAL, INDIRECT, INCIDENTAL, OR CONSEQUENTIAL
DAMAGES, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF THE USE OR INABILITY TO USE THE FONT SOFTWARE OR FROM
OTHER DEALINGS IN THE FONT SOFTWARE.


--- GSAP standard license ---
Source: https://gsap.com/standard-license/
Standard "No Charge" GSAP License
I. DEFINITIONS
“GSAP License”
means the terms and conditions of this GSAP Software License Agreement.
"GSAP Products"
means any Software made available at
gsap.com
or any successor sites, including but not limited to the GSAP animation library and related plugins, tools, or extensions.
"Permitted Uses"
means the implementation and/or use of GSAP Products on any website, web application, or digital interface by any person or entity (which may include, for clarity, those of companies that compete with Webflow in other areas of business).
"Prohibited Uses"
means any implementation and/or use of GSAP Products in tools that allow users to build visual animations without code that encourages, induces, or materially assists in creating a solution that competes with Webflow’s visual animation building capabilities.
"Competitive Products"
means any software, tool, or service that enables users to create, edit, or manage animations through a visual interface or builder similar to
Webflow
.
II. GRANT OF LICENSE
Subject to the terms and conditions of this GSAP License, Webflow grants you a non-exclusive, worldwide license to use, reproduce, display, and implement GSAP Products solely for Permitted Uses.
III. RESTRICTIONS
You may not:
Use any GSAP Products for any Prohibited Uses without prior written consent;
Reverse engineer any GSAP Products for the purpose of creating Competitive Products;
Remove or alter any proprietary notices or branding from GSAP Products.
IV. OWNERSHIP AND INTELLECTUAL PROPERTY
All intellectual property rights in GSAP Products, including but not limited to copyright, patents, trademarks, and trade secrets, remain the exclusive property of Webflow. This GSAP License does not transfer any ownership rights in GSAP Products to you.
V. TERMINATION
Webflow may terminate this GSAP License and revoke your access in its discretion if you fail to comply with any of these terms and conditions. Upon termination, you must cease all use of GSAP Products and destroy all copies in your possession.
VI. MISCELLANEOUS PROVISIONS
General
: This GSAP License is incorporated into and subject to Webflow’s Terms of Service available
here
(
"Terms of Service"
). In the event of any conflict or inconsistency between this GSAP License and the Terms of Service, the terms of this GSAP License shall govern in relation to your use of any GSAP Products.
Amendments
: Webflow reserves the right to update or modify this GSAP License at any time by posting the revised terms on this website, provided that any such updates or modifications shall not result in any material degradation to the security, integrity, or functionality of any GSAP Products. You understand and agree that your continued use of any GSAP Products after such revisions to this GSAP License constitutes your acceptance of this GSAP License as revised. If you do not accept the revised GSAP License, you are prohibited from using versions of the GSAP Products released after the effective date of the revised GSAP License (as well as any updates made to previous versions). Notwithstanding, you may continue using previous versions of GSAP Products under the applicable terms licensed to you prior to the effective date of the revised GSAP License (for clarity, excluding any updates made thereto).
No Waiver
: Failure of Webflow to enforce any provision of this GSAP License shall not constitute a waiver of future enforcement of that or any other provision.
FAQ
Is it acceptable for AI tools like ChatGPT, Cursor, Lovable, Webstudio, etc. to generate GSAP code?
Absolutely! AI-generated code is not a "Prohibited Use".
What if a WordPress plugin or theme or other niche tool allows users to create GSAP-driven effects through a visual interface? Is that prohibited?
We want to encourage developers to build on top of GSAP, including visual tools that don't directly compete with Webflow's rich animation-building capabilities. If you are not sure if your product might be considered a "Prohibited Use", feel free to
contact us
so we can talk through it!
Can I really use GSAP in commercial projects without paying anything?
Yes, really! Commercial usage is covered under the standard license. All of GSAP including the plugins that were formerly "members-only" like
SplitText
and
MorphSVG
can be used in commercial projects at no charge. Enjoy! 💚
Effective date: April 30, 2025
Last modified date: May 30, 2025
Copyright (©) 2025, Webflow
