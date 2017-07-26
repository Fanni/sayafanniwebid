---
author: saya
comments: true
date: 2014-09-22 23:07:04+00:00
layout: post
link: http://sayafanni.web.id/?p=496
slug: setting-backlight-slackware-linux
title: Setting backlight slackware linux
wordpress_id: 496
categories:
- Kehidupan saya
- Slackware
tags:
- backlight
- elilo
- Linux
- Slackware
---

Pagi ini saya menemukan cara untuk mengatur tingkat kecerahan (_brightness_) saat pertama booting di Slackware 14.1 dengan linux kernel 3.10.17 pada leptop lenovo saya.
Caranya dengan memasukkan intel.modeset=1 dan acpi_backlight=intel_backlight ke dalam kernel parameter di file elilo.conf di direktori /boot/efi/EFI/Slackware.
Sekarang saat pertama booting, tingkat kecerahan menyesuaikan setelan kecerahan di xfce :D

Berikut ini isi file elilo.conf saya
`
chooser=simple
delay=1
timeout=1
#
image=vmlinuz
        label=vmlinuz
        read-only
        append="root=/dev/sda5 intel.modeset=1 acpi_backlight=intel_backlight ro"
`
