---
title: XSLT kodunda hata ayıklama yolları
description: Kodda adım adım ilerler, kesme noktaları ayarlamak ve XSLT yürütme Visual Studio XSLT hata ayıklayıcısını kullanarak XSLT kodunda hata ayıklamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8038c954ff4abe447418247c6d99485dc081bc14299ecbc2c3a5c29b93cccba9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351116"
---
# <a name="debugging-xslt"></a>XSLT Hatalarını Ayıklama

XSLT kodunda hata ayıklamak için Visual Studio. XSLT hata ayıklayıcısı kesme noktaları ayarlamayı, XSLT yürütme durumları görüntülemeyi ve bu gibi durumları destekler. XSLT hata ayıklayıcısı, XSLT stil sayfalarında veya XSLT uygulamalarında hata ayıklamak için kullanılabilir.

Kodun içine adım atarak, üzerine atarak veya koddan çıkararak kodu tek tek yürütebilirsiniz. XSLT hata ayıklayıcısının kod adımlama işlevini kullanma komutları, diğer hata ayıklayıcıları için Visual Studio aynıdır.

Hata ayıklamaya başladıktan sonra XSLT hata ayıklayıcısı giriş belgesini ve XSLT çıkışını göstermek için pencereleri açar.

> [!NOTE]
> XSLT hata ayıklayıcısı yalnızca Professional ve Enterprise sürümlerinde Visual Studio.

## <a name="debug-from-the-xml-editor"></a>XML düzenleyicisinden hata ayıklama

Düzenleyicide bir stil sayfası veya bir giriş XML dosyası açık olduğunda hata ayıklayıcıyı başlatabilirsiniz. Bu, stil sayfası tasarlarken hata ayıklamaya olanak sağlar.

1. Stil sayfası veya XML dosyasını Visual Studio.

1. XML **menüsünden XSLT Hata Ayıklamayı** Başlat'ı **seçin** veya Alt  + **F5 tuşuna basın.**

## <a name="debug-from-an-app-that-uses-xslt"></a>XSLT kullanan bir uygulamada hata ayıklama

Bir uygulamada hata ayıklarken XSLT'ye adım atabilirsiniz. Bir çağrıda **F11'e** <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> basıyorken hata ayıklayıcı XSLT koduna adım atabilir.

> [!NOTE]
> sınıfından <xref:System.Xml.Xsl.XslTransform> XSLT'ye adımlama desteklenmiyor. sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform> hata ayıklama sırasında XSLT'ye adımlamayı destekleyen tek XSLT işlemcidir.

### <a name="to-start-debugging-an-xslt-application"></a>XSLT uygulamasında hata ayıklamaya başlamak için

1. Nesnesinin örneğini <xref:System.Xml.Xsl.XslCompiledTransform> oluştururken, `enableDebug` kodunda `true` parametresini olarak ayarlayın. Bu, XSLT işlemcisinin kod derlenmiş olduğunda hata ayıklama bilgileri oluşturmasını söyler.

1. XSLT koduna adımını atarak **F11** tuşuna basın.

   XSLT stil sayfası yeni bir belge penceresine yüklenir ve XSLT hata ayıklayıcısı başlatılır.

   Alternatif olarak stil tablosuna bir kesme noktası ekleyebilir ve uygulamalarınızı çalıştırabilirsiniz.

### <a name="example"></a>Örnek

Aşağıda bir C# XSLT programı örneği yer almaktadır. XSLT hata ayıklamasını etkinleştirmeyi gösterir.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT profil oluşturucusu

[XSLT profilleyici,](../xml-tools/xslt-profiler.md) geliştiricilerin ayrıntılı XSLT performans raporları oluşturarak XSLT kodundaki performansla ilgili sorunları ölçmesini, değerlendirmesini ve hedeflemesini sağlayan bir araçtır. Daha fazla bilgi için [bkz. XSLT profilleyicisi.](../xml-tools/xslt-profiler.md)

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Hata ayıklayıcının Visual Studio bakın](../debugger/debugger-feature-tour.md)
- [Hata ayıklamanın temelleri: Kesme noktaları](../debugger/using-breakpoints.md)
