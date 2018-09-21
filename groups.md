---
layout: default
title: Group List
---
<table class="ui tablet stackable table">
  <thead>
    <tr>
      <th>Name</th>
      <th><i class="world icon"></i></th>
      <th><i class="twitter icon"></i></th>
      <th><i class="envelope icon"></i></th>
      <th><i class="facebook icon"></i></th>
      <th><i class="info icon"></i></th>
      <th>Location</th>
      <th>Calendar</th>
    </tr>
  </thead>
  <tbody>
{% assign groups = site.data.groups | sort %}
{% for group_hash in groups %}
{% assign group = group_hash[1] %}
    <tr>
      <td>{{ group.name|default('WARNING: NOT SET NAME') }}</td>
      <td>{% if group.website|default('') != '' %}<a href="{{ group.website }}" target="_new"><i class="circular world icon"></i></a>{% endif %}</td>
      <td>{% if group.twitter|default('') != '' %}<a href='https://twitter.com/{{ group.twitter }}' target='_new'><i class="circular twitter icon"></i></a>{% endif %}</td>
      <td>{% if group.email|default('') != '' %}<a href='mailto:{{ group.email }}'><i class="circular envelope icon"></i></a>{% endif %}</td>
      <td>{% if group.facebook|default('') != '' %}<a href='https://facebook.com/{{ group.facebook }}' target='_new'><i class="circular facebook icon"></i></a>{% endif %}</td>
      <td>{% if group.description|default('') != '' %}<i class="circular info icon link" data-content="{{ group.description }}" data-variation="very wide"></i>{% endif %}</td>
      <td><i class="marker icon"></i>{{ group.where|default('WARNING: NOT SET LOCATION') }}</td>
      <td><i class="calendar icon"></i>{{ group.when|default('WARNING: NOT SET WHEN') }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>

<script>
  $('.circular.icon.link').popup({
    inline: true
  });
</script>

