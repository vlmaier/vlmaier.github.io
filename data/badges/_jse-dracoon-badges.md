{% capture badges %}
{% include_relative data/badges/vagrant.md %}
{% include_relative data/badges/unix.md %}
{% include_relative data/badges/python.md %}
{% include_relative data/badges/scala.md %}
{% include_relative data/badges/mariadb.md %}
{% include_relative data/badges/jira.md %}
{% include_relative data/badges/git.md %}
{% include_relative data/badges/swagger.md %}
{% include_relative data/badges/pycharm.md %}

{% endcapture %}
{{ badges | markdownify }}

<div style="clear:both;"></div>
