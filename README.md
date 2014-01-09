## Remark

Presentations are done using [remark](https://github.com/gnab/remark). To get started:

- Drag --> [Slideshow](javascript:(function()%20{%20%20%20%20var%20GIST_FILE_PATTERN%20=%20/^\/([^\/]+)\/(\d+)$/;%20%20%20%20var%20REPO_FILE_PATTERN%20=%20/^\/([^\/]+)\/([^\/]+)\/tree\/([^\/]+)\/([^\/]+)$/;%20%20%20%20var%20hostname%20=%20document.location.hostname;%20%20%20%20var%20path%20%20%20%20%20=%20document.location.pathname;%20%20%20%20var%20slides%20%20%20=%20'http://remarks.sinaapp.com/';%20%20%20%20var%20match%20%20%20%20=%20null;%20%20%20%20%20%20%20%20if%20(hostname%20===%20'gist.github.com'%20&&%20(match%20=%20path.match(GIST_FILE_PATTERN)))%20{%20%20%20%20%20%20%20%20slides%20=%20slides%20+%20'gist/'%20+%20match[2];%20%20%20%20%20}%20else%20if%20((hostname%20===%20'www.github.com'%20||%20hostname%20===%20'github.com')%20&&%20(match%20=%20path.match(REPO_FILE_PATTERN)))%20{%20%20%20%20%20%20%20%20slides%20=%20slides%20+%20'repo/'%20+%20match[1]%20+%20'/'%20+%20match[2]%20+%20'/'%20+%20match[4]%20+%20'/?branch='%20+%20match[3];%20%20%20%20%20}%20else%20{%20%20%20%20%20%20%20%20alert('Not%20a%20valid%20remarks%20slides');%20%20%20%20%20}%20%20%20%20window.open(slides,%20'_blank','width=600,height=400');})();) to your bookmark bar.
- Navigate to [using_remark](https://github.com/johnschult/tts/tree/master/using_remark) and click on the **Slideshow** bookmarklet.
- Page through the slideshow to get an idea of what you can do with **remark**.

New presentations should be in their own folder and should be named ``slides.md``.
