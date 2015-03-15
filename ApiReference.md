# API Reference #

## class org.mozilla.universalchardet.UniversalDetector ##

### public UniversalDetector(CharsetListener listener) ###
Constructs a detector. `listener` is a listener object that is notified of the detected charset. `listener` can be `null`.

### public boolean isDone() ###
Returns whether the detector has detected a charset.

### public String getDetectedCharset() ###
If the detector has detected an encoding, returns one of the charset names defined in org.mozilla.universalchardet.Constants. If the detector has not detected any encoding yet, returns `null`.

### public void handleData(final byte[.md](.md) buf, int offset, int length) ###
Feeds data to the detector.

### public void dataEnd() ###
Notifies the detector that there are no more data to process. This method should be always called before you call getDetectedCharset().

### public void reset() ###
Resets the detector. After reset(), you can reuse the detector to process another document.


## class org.mozilla.universalchardet.Constants ##
All charset names that juniversalchardet can detect are defined in this class.

  * Charsets supported by Java
    * public static final String CHARSET\_ISO\_2022\_JP
    * public static final String CHARSET\_ISO\_2022\_CN
    * public static final String CHARSET\_ISO\_2022\_KR
    * public static final String CHARSET\_ISO\_8859\_5
    * public static final String CHARSET\_ISO\_8859\_7
    * public static final String CHARSET\_ISO\_8859\_8
    * public static final String CHARSET\_BIG5
    * public static final String CHARSET\_GB18030
    * public static final String CHARSET\_EUC\_JP
    * public static final String CHARSET\_EUC\_KR
    * public static final String CHARSET\_EUC\_TW
    * public static final String CHARSET\_SHIFT\_JIS
    * public static final String CHARSET\_IBM855
    * public static final String CHARSET\_IBM866
    * public static final String CHARSET\_KOI8\_R
    * public static final String CHARSET\_MACCYRILLIC
    * public static final String CHARSET\_WINDOWS\_1251
    * public static final String CHARSET\_WINDOWS\_1252
    * public static final String CHARSET\_WINDOWS\_1253
    * public static final String CHARSET\_WINDOWS\_1255
    * public static final String CHARSET\_UTF\_8
    * public static final String CHARSET\_UTF\_16BE
    * public static final String CHARSET\_UTF\_16LE
    * public static final String CHARSET\_UTF\_32BE
    * public static final String CHARSET\_UTF\_32LE

  * Charsets NOT supported by Java
    * public static final String CHARSET\_HZ\_GB\_2312
    * public static final String CHARSET\_X\_ISO\_10646\_UCS\_4\_3412
    * public static final String CHARSET\_X\_ISO\_10646\_UCS\_4\_2143