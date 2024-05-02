Welcome!

This file is a description of the JavaDoc eXtra files added
(because Oracle missed things).

Besides information generated from the source to be processed,
JDK 8-generated JavaDoc JARs contain:
• script.js (probably trivial, no licence statement, but an
  antecessor to the same file in later versions as below)
• stylesheet.css (“Javadoc style sheet”), no statement
  (which references a DejaVu file not included)

JDK 11-generated JavaDoc JARs contain:
• two copies of jQuery 3.5.1 (identical, not minified)
  which embeds Sizzle.js (both MIT-licenced), with copyright
  statement and licence indicator but the actual licence text
  is missing
• jQuery UI 1.12.1 (+ jQuery UI Autocomplete, Keycode, Menu,
  Position, Structure, Unique ID, Widget) in both minified and
  nōn-minified form (CSS + JS) with statements but no MIT text
• JSZip 3.7.1 (which embeds pako), both under MIT (JSZip also
  optionally GPLv3 but can be ignored here), minified and not;
  JSZip statement is there, pako is missing so reproduce it here:
    Copyright (C) 2014-2017 by Vitaly Puzrin and Andrei Tuputcyn
• JSZipUtils (+ IE), same as above, 0.0.2 actually…
• script.js (see above) and search.js, now with Oracle GPLv2 with
  "Classpath" exception; full text of the licence and the exception
  are missing, though (for JDK 8: script.js is © 2013, 2018 Oracle
  and/or its affiliates)
• stylesheet.css (see above)

JDK 17 fixed this half-arsed:
• legal/ASSEMBLY_EXCEPTION was supposed to contain the "Classpath"
  exception but instead contains the "Assembly" exception, which
  is useless here; still lacks the text of the GPLv2 as well
• legal/jquery.md + legal/jqueryUI.md contain full information for
  jQuery+Sizzle, jQuery UI and the versions even match
• jquery-ui.overrides.css (GPLv2+CE by Oracle)
• script.js, search.js like in 11 but newer
• stylesheet.css, still unmarked
• jQuery stuff was moved to script-dir/ with only minified forms
  being shipped now, probably to save space
• JSZip/JSZipUtils are gone

There are also a couple of icon images present other than those
from jQuery UI. They are very small and trivial and not addressed
by upstream, when I reported MJAVADOC-669 and JDK-8259530 for this;
nor is the CSS addressed.

JDK 21 is mostly the same as JDK 17 plus:
• new (SVG) icons under GPL+CE referring to a LICENSE file supposed
  to accompany this (but is not, see below for COPYING, EXCEPTION)
• search-page.js: dito

So we’ve got these issues:
• resources/glass.png, resources/x.png, stylesheet.css upstream
  ‣ assume GPLv2+CE like the rest of the JDK
• GPL licence body missing in 8/11/17/21-generated JARs
  ‣ provided as COPYING, the directory substituting LICENSE
• "Classpath" exception actual text missing in 8/11-generated JARs
  and wrong text in 17/21-generated JARs
  ‣ provided as EXCEPTION
• MIT licence body missing in 8/11-generated JARs
  ‣ provided as LICENCE.MIT
• some author/copyright/grants missing (8: script.js, 11: pako)
  ‣ provided inline above
• minification
  ‣ not a licence problem; redistribution is fine, and generated
    JavaDoc JARs with these extra files embedded are fully FOSS
    (of course only if the underlying project is), just a binary
    redistribution
  ‣ at least they (other than jquery-ui.min.js as the generator
    seemingly switched to a different compressor/minifyer) are
    unmodified/identical with the upstream releases
    ⇒ ideally, find out the minifyer they used in 2018, redo with
      the jquery-ui.js (which i̲s̲ identical) from the JAR, compare
• other JDK releases not tested
