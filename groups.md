---
layout: default
title: Group List
---
<table>
  <thead>
    <tr>
      <th>Info</th>
      <th>Name</th>
      <th>Website</th>
      <th>Social</th>
      <th>Location</th>
      <th>Calendar</th>
    </tr>
  </thead>
  <tbody>
{% for group_hash in site.data.groups | sort %}
{% assign group = group_hash[1] %}
    <tr>
      <td>{% if group.description|default('') != '' %}<i class="circular info icon link" data-content="{{ group.description }}" data-variation="very wide"></i>{% endif %}</td>
      <td>{{ group.name|default('WARNING: NOT SET NAME') }}</td>
      <td>{% if group.website|default('') != '' %}<a href="{{ group.website }}" target="_new"><i class="world icon"></i></a>{% endif %}</td>
      <td>{% if group.twitter|default('') != '' %}<a href='https://twitter.com/{% if group.twitter[:1] == "@" %}{{ group.twitter[1:] }}{% else %}{{ group.twitter }}{% endif %}' target='_new'><i class="blue twitter icon"></i></a>{% endif %}{% if group.email|default('') != '' %}<a href='mailto:{{ group.email }}'><i class="grey envelope icon"></i></a>{% endif %}{% if group.facebook|default('') != '' %}<a href='https://facebook.com/{{ group.facebook }}' target='_new'><i class="blue facebook icon"></i></a>{% endif %}</td>
      <td><i class="marker icon"></i>{{ group.where|default('WARNING: NOT SET LOCATION') }}</td>
      <td><i class="calendar icon"></i>{{ group.when|default('WARNING: NOT SET WHEN') }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>
