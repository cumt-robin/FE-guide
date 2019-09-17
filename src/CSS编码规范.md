# CSS编码规范

TODO

<div id="gitalk-container"></div>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
<script>
var gitalk = new Gitalk({
    clientID: "abe61bb2112d4926d0b9",
    clientSecret: "760737a207de2813a6586e1d2c14dd187ddeea64",
    repo: "FE-guide",
    owner: "cumt-robin",
    admin: ["cumt-robin"],
    id: decodeURIComponent(location.pathname)
});
gitalk.render("gitalk-container");
</script>