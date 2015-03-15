# Release Note #

## 1.0.3 ##
  * Fixed wrong method calls in Big5Prober#handleData, EUCTWProber#handleData, GB18030Prober#handleData. Thanks, Lersh99.
  * Fixed build.xml to emit Java1.5-compatible bytecode. Thanks, lnezda.
  * Included TestDetector.java in the source package. Thanks, lnezda.

## 1.0.2 ##
  * Canonicalized charset names which are returned by UniversalDetector.getDetectedCharset().
  * All charset names which juniversalchardet can detect are now defined in org.mozilla.universalchardet.Constants. They can be compared to the result of UniversalDetector.getDetectedCharset().
  * Added SWIG interface.

## 1.0.1 ##
  * Fixed an array bound violation in ISO2022JPSMModel. Thanks, Kazutoshi Satoda.

## 1.0 ##
  * Initial release.