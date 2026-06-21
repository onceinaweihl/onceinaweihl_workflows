# Changelog

## [1.9.1](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.9.0...v1.9.1) (2026-06-21)


### Bug Fixes

* author release PR with app token so it triggers downstream workflows ([#17](https://github.com/onceinaweihl/onceinaweihl_workflows/issues/17)) ([3eded15](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/3eded155ccc8c2a1baf50c579bbf6be15101aeac))

## [1.9.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.8.0...v1.9.0) (2026-06-05)


### Features

* **ci:** make Android debug build opt-out via run_android_build ([13de7dd](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/13de7dd07330835055b89ab04aaeb661ebf0ebef))
* **ci:** make Android debug build opt-out via run_android_build ([ec8c163](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/ec8c163c6447fd02b1061f0374d0b96397af0cb0))
* **reusable-release-notes:** aggregate per-PR notes onto release PR ([ec24bb9](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/ec24bb9c3f19335fd6072bf233e255654fc61058))
* **reusable-release-notes:** aggregate per-PR notes onto release PR ([a38412b](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/a38412bcad98f4c959b54cb50b5e8f1904ba3ded))

## [1.8.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.7.0...v1.8.0) (2026-05-14)


### Features

* add reusable security-nightly workflow + template wrapper ([8ffb357](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/8ffb3571ccc2d394802fc6ea53a08a2577fe9c51))
* **reusable-security-nightly:** add daily Trivy scan workflow ([092e6c5](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/092e6c533478e9285883078ef0bddf5a57a174cd))
* **template:** add security-nightly wrapper for new apps ([ee1f31d](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/ee1f31d095e70554de2fcafad302836fd98ba491))

## [1.7.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.6.0...v1.7.0) (2026-05-14)


### Features

* **reusable-ci:** add Trivy security scan job ([4ded8d2](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/4ded8d2138559614dc1874b2a7a99d351c97c900))
* **reusable-ci:** add Trivy security scan job ([4d58cc5](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/4d58cc5e8cb10e5290e1d565b3ba288197f34cc9))

## [1.6.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.5.0...v1.6.0) (2026-05-09)


### Features

* **reusable-build-android-apk:** add manual APK build workflow ([34f6723](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/34f672366333105b0a2995c162200f1f6967e807))
* **reusable-build-android-apk:** add manual APK build workflow ([943c4bf](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/943c4bf8d06ab46238b69a8375e25ac6e0cea124))

## [1.5.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.4.0...v1.5.0) (2026-05-08)


### Features

* **autofix:** support workflow_dispatch alongside pull_request events ([1f906d9](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/1f906d9f618f7a356ce6add7d11f174f5b732e39))

## [1.4.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.3.0...v1.4.0) (2026-05-06)


### Features

* **regenerate-codegen:** also commit pubspec.lock ([b80fdb4](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/b80fdb43b03864c98b9eebee8dbb47fe886319b6))

## [1.3.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.2.0...v1.3.0) (2026-05-05)


### Features

* **actions/setup-core-auth:** expose minted token as output ([6869a7a](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/6869a7a30e9f510675c1c989a35305979526e370))
* **actions/setup-core-auth:** parametrize repositories input ([dbd5537](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/dbd5537bc2fe645a72a6faf76f08e381cd4051d2))
* **reusable-regenerate-codegen:** also regenerate flutter gen-l10n output ([4a9fec0](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/4a9fec01a8b8456cce8d2be2c67a3082cabd4d6b))


### Bug Fixes

* declare CORE_ACCESS_APP_KEY as named secret in reusable workflow ([fc5ac03](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/fc5ac03df3e5980a702efd0291abfe1d2b164b77))

## [1.2.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.1.0...v1.2.0) (2026-05-04)


### Features

* add reusable-regenerate-codegen workflow ([2582d25](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/2582d25cf204e9fbadc3bfa7b9e2a80ea3c07fc5))

## [1.1.0](https://github.com/onceinaweihl/onceinaweihl_workflows/compare/v1.0.0...v1.1.0) (2026-04-26)


### Features

* add renovate autofix reusable workflow ([ba75a33](https://github.com/onceinaweihl/onceinaweihl_workflows/commit/ba75a33850c430bc67803407d6eb561fb88e2349))
