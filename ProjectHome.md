# 1. What is it? #
juniversalchardet is a Java port of 'universalchardet',
that is the encoding detector library of Mozilla.

The original code of universalchardet is available at
http://lxr.mozilla.org/seamonkey/source/extensions/universalchardet/

Techniques used by universalchardet are described at
http://www.mozilla.org/projects/intl/UniversalCharsetDetection.html


# 2. Encodings that can be detected #
  * Chinese
    * ISO-2022-CN
    * BIG5
    * EUC-TW
    * GB18030
    * HZ-GB-2312<sup>1</sup>

  * Cyrillic
    * ISO-8859-5
    * KOI8-R
    * WINDOWS-1251
    * MACCYRILLIC
    * IBM866
    * IBM855

  * Greek
    * ISO-8859-7
    * WINDOWS-1253

  * Hebrew
    * ISO-8859-8
    * WINDOWS-1255

  * Japanese
    * ISO-2022-JP
    * SHIFT\_JIS
    * EUC-JP

  * Korean
    * ISO-2022-KR
    * EUC-KR

  * Unicode
    * UTF-8
    * UTF-16BE / UTF-16LE
    * UTF-32BE / UTF-32LE / X-ISO-10646-UCS-4-3412<sup>1</sup> / X-ISO-10646-UCS-4-2143<sup>1</sup>

  * Others
    * WINDOWS-1252

**1** Currently not supported by Java

# 3. How to use it #
  1. Construct an instance of org.mozilla.universalchardet.UniversalDetector.
  1. Feed some data (typically several thousands bytes) to the detector by calling UniversalDetector.handleData().
  1. Notify the detector of the end of data by calling UniversalDetector.dataEnd().
  1. Get the detected encoding name by calling UniversalDetector.getDetectedCharset().
  1. Don't forget to call UniversalDetector.reset() before you reuse the detector instance.


---

## Sample Code ##
[Download](http://juniversalchardet.googlecode.com/svn/trunk/example/TestDetector.java)
```
import org.mozilla.universalchardet.UniversalDetector;

public class TestDetector {
  public static void main(String[] args) throws java.io.IOException {
    byte[] buf = new byte[4096];
    String fileName = args[0];
    java.io.FileInputStream fis = new java.io.FileInputStream(fileName);

    // (1)
    UniversalDetector detector = new UniversalDetector(null);

    // (2)
    int nread;
    while ((nread = fis.read(buf)) > 0 && !detector.isDone()) {
      detector.handleData(buf, 0, nread);
    }
    // (3)
    detector.dataEnd();

    // (4)
    String encoding = detector.getDetectedCharset();
    if (encoding != null) {
      System.out.println("Detected encoding = " + encoding);
    } else {
      System.out.println("No encoding detected.");
    }

    // (5)
    detector.reset();
  }
}
```

# 4. Related Works #
## jchardet ##
  * http://jchardet.sourceforge.net/
jchardet is another Java port of the Mozilla's encoding dectection library.
The main difference between jchardet and juniversalchardet is modules
they are based on. jchardet is based on the 'chardet' module that has
long existed. juniversalchardet is based on the 'universalchardet' module
that is new and generally provides better accuracy on detection results.


# 5. License #
The library is subject to the Mozilla Public License Version 1.1.
Alternatively, the library may be used under the terms of either
the GNU General Public License Version 2 or later, or the GNU
Lesser General Public License 2.1 or later.