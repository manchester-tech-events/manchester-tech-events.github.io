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
{% assign conferences = site.data.conferences | sort %}
{% for conference_hash in conferences %}
{% assign conference = conference_hash[1] %}
    <tr>
      <td>{{ conference.name|default('WARNING: NOT SET NAME') }}</td>
      <td>{% if conference.website|default('') != '' %}<a href="{{ conference.website }}" target="_new"><i class="circular world icon"></i></a>{% endif %}</td>
      <td>{% if conference.twitter|default('') != '' %}<a href='https://twitter.com/{{ conference.twitter }}' target='_new'><i class="circular twitter icon"></i></a>{% endif %}</td>
      <td>{% if conference.email|default('') != '' %}<a href='mailto:{{ conference.email }}'><i class="circular envelope icon"></i></a>{% endif %}</td>
      <td>{% if conference.facebook|default('') != '' %}<a href='https://facebook.com/{{ conference.facebook }}' target='_new'><i class="circular facebook icon"></i></a>{% endif %}</td>
      <td>{% if conference.description|default('') != '' %}<i class="circular info icon link" data-content="{{ conference.description }}" data-variation="very wide"></i>{% endif %}</td>
      <td><i class="marker icon"></i>{{ conference.where|default('WARNING: NOT SET LOCATION') }}</td>
      <td><i class="calendar icon"></i>{{ conference.when|default('WARNING: NOT SET WHEN') }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>

<script>
  $('.circular.icon.link').popup({
    inline: true
  });
</script>

