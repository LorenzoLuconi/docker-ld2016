= Generatore di slide via asciidoc + revealjs

Viene utilizzato asciidoctor con template revealjs per creare le presentazioni
web.

== Auto ri-compilazione via gradle

./gradlew asciidoctor -t

== Setup di asciidoctor

In shell:
 gem install --user-install asciidoctor tilt thread_safe slim
 cd ~/git # o directory qualsiasi
 git clone git://github.com/asciidoctor/asciidoctor-reveal.js.git

In questo progetto (o simile):
 curl -L https://github.com/hakimel/reveal.js/archive/3.3.0.tar.gz | tar xzf -
 mv reveal.js{-3.3.0,}

=== Per compilare

 asciidoctor -T ~/git/asciidoctor-reveal.js/templates/slim src/docs/docker-ld2016.txt

== Setup emacs

$ cat >> .emacs <<EOF
(when (>= emacs-major-version 24)
  (require 'package)
  (add-to-list
   'package-archives
   '("melpa" . "http://melpa.org/packages/")
   t)
  (package-initialize))
(setq-default fill-column 78)
EOF

In emacs:
 M-x package-install RET adoc-mode RET

E nel buffer specifico poi (docker-ld2016.txt):
 M-x adoc-mode
