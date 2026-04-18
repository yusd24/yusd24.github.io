---
layout: page
permalink: /seminar/
title: Seminars
description: 
nav: true
nav_order: 5
---

Schedules for seminars, workshops, or conferences.

  <div class="post mt-4">
    <h2 class="mb-3"><i class="fas fa-calendar-alt"></i> Upcoming Events</h2>

    <div class="calendar-wrapper" id="calendar-container" style="display: none;">
      <iframe
        id="calendar-iframe"
        data-calendar-id="{{ include.calendar_id }}"
        data-timezone="{{ include.timezone | default: 'UTC' }}"
        style="{{ include.style | default: 'border:0; width:100%; height:600px;' }}"
        frameborder="0"
        scrolling="no"
      >
      </iframe>
    </div>
  </div>
