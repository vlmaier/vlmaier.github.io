{% capture badges %}
{% include_relative data/badges/maven.md %}
{% include_relative data/badges/macos.md %}
{% include_relative data/badges/mariadb.md %}
{% include_relative data/badges/unix.md %}
{% include_relative data/badges/java.md %}
{% include_relative data/badges/postman.md %}
{% include_relative data/badges/jwt.md %}
{% include_relative data/badges/gitlab-ci.md %}
{% include_relative data/badges/junit.md %}
{% include_relative data/badges/spring.md %}
{% include_relative data/badges/vs-code.md %}
{% include_relative data/badges/jira.md %}
{% include_relative data/badges/git.md %}
{% include_relative data/badges/swagger.md %}
{% include_relative data/badges/idea.md %}
{% include_relative data/badges/markdown.md %}
{% include_relative data/badges/thymeleaf.md %}
{% include_relative data/badges/s3.md %}
{% include_relative data/badges/rabbitmq.md %}
{% include_relative data/badges/docker.md %}

{% endcapture %}
{{ badges | markdownify }}

<div style="clear:both;"></div>
