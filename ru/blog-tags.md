---
layout : default
title : Блог Андрея Акиньшина / Теги
permalink: /ru/blog/tags/index.html
---
@model Pretzel.Logic.Templating.Context.PageContext

<h2>Теги</h2>
<div>
@foreach(var tag in Model.Site.Tags.OrderByDescending(c => c.Posts.Count()))
{
    var posts = tag.Posts.Distinct().ToList();
    if (posts.Count() > 0)
    {
        <h4 id="@tag.Name"><a href="#@tag.Name">#</a>@tag.Name</h4>
        <ul>
        @foreach(var post in posts)
        {
            <li><a href='@post.Url.Replace("index.html", "")'>@post.Title</a></li>
        }
        </ul>
    }
}
</div>