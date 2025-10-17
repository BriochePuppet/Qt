# Build Qt Static Library with XCB backend support  

[Qt 5.15](https://github.com/qt/qt5/commit/c59ae95d8aed879768fe09e0de04f693724e6319)  

```diff
From b3e0270e3602541b783b962c6a8b34f75f29d714 Mon Sep 17 00:00:00 2001
From: HanetakaChou <HanetakaChou@outlook.com>
Date: Fri, 17 Oct 2025 21:59:35 +0200
Subject: [PATCH] qt_configure_prefix_path_str

---
 configure.pri | 6 +++---
 1 file changed, 3 insertions(+), 3 deletions(-)

diff --git a/configure.pri b/configure.pri
index 365a16403eb..6cca132d55a 100644
--- a/configure.pri
+++ b/configure.pri
@@ -899,10 +899,10 @@ defineTest(qtConfOutput_preparePaths) {
 
     $${currentConfig}.output.qconfigSource = \
         "/* Installation Info */" \
-        "static const char qt_configure_prefix_path_str  [12+256] = \"qt_prfxpath=$$config.input.prefix\";" \
+        "static const char qt_configure_prefix_path_str  [12+256] = \"qt_prfxpath=/usr\";" \
         "$${LITERAL_HASH}ifdef QT_BUILD_QMAKE" \
-        "static const char qt_configure_ext_prefix_path_str   [12+256] = \"qt_epfxpath=$$config.input.extprefix\";" \
-        "static const char qt_configure_host_prefix_path_str  [12+256] = \"qt_hpfxpath=$$config.input.hostprefix\";" \
+        "static const char qt_configure_ext_prefix_path_str   [12+256] = \"qt_epfxpath=/usr\";" \
+        "static const char qt_configure_host_prefix_path_str  [12+256] = \"qt_hpfxpath=/usr\";" \
         "$${LITERAL_HASH}endif" \
         "" \
         "static const short qt_configure_str_offsets[] = {" \
-- 
2.47.3
```

```bash
mkdir ./build

cd ./build

../configure \
-prefix "install" \
-opensource \
-confirm-license \
-release \
-static \
-platform linux-clang \
-c++std c++17 \
-sse2 \
-sse3 \
-ssse3 \
-sse4.1 \
-sse4.2 \
-avx \
-avx2 \
-no-avx512 \
-nomake examples \
-nomake tests \
-eventfd \
-inotify \
-no-feature-concurrent \
-no-dbus \
-no-feature-network \
-no-feature-sql \
-no-feature-testlib \
-no-feature-xml \
-qt-zlib \
-no-zstd \
-no-glib \
-no-icu \
-no-journald \
-no-syslog \
-no-slog2 \
-qt-pcre \
-qt-freetype \
-no-fontconfig \
-qt-harfbuzz \
-qt-libjpeg \
-qt-libpng \
-no-feature-texthtmlparser \
-no-feature-cssparser \
-no-feature-textodfwriter \
-no-feature-textmarkdownreader \
-no-feature-textmarkdownwriter \
-no-egl \
-no-openvg \
-no-opengl \
-no-vulkan \
-no-feature-sessionmanager \
-qpa xcb \
-no-xcb-xlib \
-no-libudev \
-no-evdev \
-no-imf \
-no-libinput \
-no-mtdev \
-no-tslib \
-xkbcommon \
-no-directfb \
-no-eglfs \
-no-gbm \
-no-kms \
-no-linuxfb \
-xcb \
-no-gtk \
-qt-tiff \
-qt-webp \
-no-cups \
-no-feature-printer \
-no-feature-printdialog \
-no-feature-printpreviewdialog \
-skip qt3d \
-skip qtactiveqt \
-skip qtandroidextras \
-skip qtcanvas3d \
-skip qtcharts \
-skip qtconnectivity \
-skip qtdatavis3d \
-skip qtdeclarative \
-skip qtdoc \
-skip qtdocgallery \
-skip qtfeedback \
-skip qtgamepad \
-skip qtgraphicaleffects \
-skip qtlocation \
-skip qtlottie \
-skip qtmacextras \
-skip qtmultimedia \
-skip qtnetworkauth \
-skip qtpim \
-skip qtpurchasing \
-skip qtquick3d \
-skip qtquickcontrols \
-skip qtquickcontrols2 \
-skip qtquicktimeline \
-skip qtremoteobjects \
-skip qtscript \
-skip qtscxml \
-skip qtsensors \
-skip qtserialbus \
-skip qtserialport \
-skip qtspeech \
-skip qtsystems \
-skip qttools \
-skip qttranslations \
-skip qtvirtualkeyboard \
-skip qtwayland \
-skip qtwebchannel \
-skip qtwebengine \
-skip qtwebglplugin \
-skip qtwebsockets \
-skip qtwebview \
-skip qtwinextras \
-skip qtx11extras \
-skip qtxmlpatterns

make -j$(nproc) install
```
