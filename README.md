meters.lv2 - Audio Level Meters
===============================

meters.lv2 is a collection of audio-level meters with GUI in LV2 plugin format.

It includes needle style meters (mono and stereo variants)

*   IEC 60268-10 Type I / DIN
*   IEC 60268-10 Type I / Nordic
*   IEC 60268-10 Type IIa / BBC
*   IEC 60268-10 Type IIb / EBU
*   IEC 60268-17 / VU

and the following stereo plugins

*   Stereo Phase Correlation Meter (Needle Display)
*   EBU R128 Meter with Histogram and History
*   Digital True-Peak Meter (4x Oversampling)
*   Goniometer (Stereo Phase Scope)
*   31 Band Spectrum-Analyzer

Currently the plugins come in both Gtk and openGL variants (both
versions are installed in parallel).


Install
-------

Compiling these plugin requires the LV2 SDK, gnu-make, a c-compiler,
gtk+2.0, libpango, libcairo and openGL (sometimes called: glu, glx, mesa).

```bash
  git clone git://github.com/x42/meters.lv2.git
  cd meters.lv2
  make
  sudo make install PREFIX=/usr
  
  # test run
  jalv.gtk 'http://gareus.org/oss/lv2/meters#DINmono_gtk'
```

Note to packagers: The Makefile honors `PREFIX` and `DESTDIR` variables as well
as `CFLAGS`, `LDFLAGS` and `OPTIMIZATIONS` (additions to `CFLAGS`).


Note on build-dependencies
--------------------------

These plugins count on rather recent (Jan 2013) fixes^Wfeatures of
some libraries (but may work with older versions too):

In particular multi-threading in cairo, pixman and pango.
Versions of those libraries earlier than libcairo < 1.12.10,
libpixman < 0.30.2 and libpango < 1.32.6 are not thread-safe.
As with all concurrency issues, things may or may not work and
if you only open one meter GUI at a time it's usually fine.

Also note that the plugins use the LV2 idle-interface (lv2 >= 1.4.2)
The plugin-host (eg. ardour or qtractori) needs to be compiled with
this or a later version of the LV2 SDK to support the features.

The plugin-host must also support http://lv2plug.in/ns/ext/resize-port/

At the time of writing Ardour 3.4 and jalv.gtk do fulfill these criteria.


Screenshots
-----------

![screenshot](https://raw.github.com/x42/meters.lv2/master/doc/LV2ebur128.png "EBU R128 Meter GUI")
![screenshot](https://raw.github.com/x42/meters.lv2/master/doc/LV2meters.png "Various Needle Meters in Ardour")

