---
title: XSLT kodunda hata ayıklamanın yolları
ms.date: 03/05/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: bb358efb711211d58525afb8d30d5cb4cad6b2e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646080"
---
# <a name="debugging-xslt"></a>XSLT Hatalarını Ayıklama

Visual Studio 'da XSLT kodunda hata ayıklaması yapabilirsiniz. XSLT hata ayıklayıcısı, kesme noktaları ayarlamayı, XSLT yürütme durumlarını görüntülemeyi ve daha fazlasını destekler. XSLT hata ayıklayıcısı XSLT stil sayfaları veya XSLT uygulamalarında hata ayıklamak için kullanılabilir.

Kodu Adımlama, Adımlama veya dışarı atlama yoluyla tek seferde bir satırı çalıştırabilirsiniz. XSLT hata ayıklayıcısı 'nın kod Adımlama işlevini kullanma komutları, diğer Visual Studio hata ayıklayıcıları için olanlarla aynıdır.

Hata ayıklamayı başlattığınızda, XSLT hata ayıklayıcı giriş belgesini ve XSLT çıkışını göstermek için Windows 'u açar.

> [!NOTE]
> XSLT hata ayıklayıcısı yalnızca Visual Studio 'nun Professional ve Enterprise sürümlerinde kullanılabilir.

## <a name="debug-from-the-xml-editor"></a>XML düzenleyicisinde hata ayıkla

Bir stil sayfası veya düzenleyicide açık bir giriş XML dosyanız olduğunda hata ayıklayıcıyı başlatabilirsiniz. Bu, stil sayfasını tasarlarken hata ayıklamanıza olanak sağlar.

1. Stil sayfasını veya XML dosyasını Visual Studio 'da açın.

1. **XML** menüsünde **XSLT hata ayıklamayı Başlat** ' ı seçin veya **alt** +**F5**tuşuna basın.

## <a name="debug-from-an-app-that-uses-xslt"></a>XSLT kullanan bir uygulamadan hata ayıklama

Bir uygulamada hata ayıklarken XSLT içine adım aktarabilirsiniz. @No__t_1 çağrısında **F11** tuşuna basarsanız, hata ayıklayıcı XSLT koduna ileredebilir.

> [!NOTE]
> @No__t_0 sınıfından XSLT 'ye Adımlama desteklenmez. @No__t_0 sınıfı, hata ayıklama sırasında XSLT 'de adımlamayı destekleyen tek XSLT işlemcisidir.

### <a name="to-start-debugging-an-xslt-application"></a>XSLT uygulamasında hata ayıklamaya başlamak için

1. @No__t_0 nesnesini örnekledikten sonra, `enableDebug` parametresini kodunuzda `true` olarak ayarlayın. Bu, XSLT işlemcisinin kod derlendiğinde hata ayıklama bilgileri oluşturmasını söyler.

1. XSLT koduna geçmek için **F11** tuşuna basın.

   XSLT stil sayfası yeni bir belge penceresine yüklenir ve XSLT hata ayıklayıcısı başlatılır.

   Alternatif olarak, stil sayfasına bir kesme noktası ekleyebilir ve uygulamanızı çalıştırabilirsiniz.

### <a name="example"></a>Örnek

Aşağıda C# XSLT programına bir örnek verilmiştir. XSLT hata ayıklamanın nasıl etkinleştirileceğini gösterir.

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
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT profil oluşturucusu

[XSLT Profiler](../xml-tools/xslt-profiler.md) , ayrıntılı XSLT performans raporları oluşturarak geliştiricilerin XSLT kodundaki performansla ilgili sorunları ölçmesine, değerlendirmesine ve hedeflemesini sağlayan bir araçtır. Daha fazla bilgi için bkz. [XSLT Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Visual Studio hata ayıklayıcısına ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklama temelleri: kesme noktaları](../debugger/using-breakpoints.md)
