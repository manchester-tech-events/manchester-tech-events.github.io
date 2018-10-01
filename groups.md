---
title: Groups
icon_source: https://semantic-ui.com/elements/icon.html
---
<table class="ui tablet stackable table">
  <thead>
    <tr>
      <th>Name</th>
      <th><i class="world icon"></i></th>
      <th><i class="twitter icon"></i></th>
      <th><i class="envelope icon"></i></th>
      <th><i class="facebook icon"></i></th>
      <th><i class="linkedin icon"></i></th>
      <th><i class="info icon"></i></th>
      <th>Location</th>
      <th>Calendar</th>
    </tr>
  </thead>
  <tbody>
{% assign groups = site.data.groups | sort %}
{% for group_hash in groups %}
{% assign group = group_hash[1] %}
{% assign group_name = group_hash[0] | replace: '_', ' ' %}
    <tr>
      <td>{{ group_name }}</td>
      <td>{% if group.website %}<a href="{{ group.website }}" target="_new"><i class="circular world icon"></i></a>{% endif %}</td>
      <td>{% if group.twitter %}<a href='https://twitter.com/{{ group.twitter }}' target='_new'><i class="circular twitter icon"></i></a>{% endif %}</td>
      <td>{% if group.email %}<a href='mailto:{{ group.email }}'><i class="circular envelope icon"></i></a>{% endif %}</td>
      <td>{% if group.facebook %}<a href='https://facebook.com/{{ group.facebook }}' target='_new'><i class="circular facebook icon"></i></a>{% endif %}</td>
      <td>{% if group.linkedin %}<a href='https://linkedin.com/company/{{ group.linkedin }}' target='_new'><i class="circular linkedin icon"></i></a>{% endif %}</td>
      <td>{% if group.description %}<i class="circular info icon link" data-content="{{ group.description }}" data-variation="very wide"></i>{% endif %}</td>
      <td><i class="marker icon"></i>{{ group.where|default:'WARNING: NOT SET LOCATION' }}</td>
      <td><i class="calendar icon"></i>{{ group.when|default:'WARNING: NOT SET WHEN' }}</td>
    </tr>
{% endfor %}
  </tbody>
</table>

<script>
  $('.circular.icon.link').popup({
    inline: true
  });
</script>
