---
title: XSLT kodunda hata ayıklamanın yolları
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: d8e3885aa895cec5ed080b7a8b4d22522d2e9edf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815623"
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

1. **XML** menüsünde **XSLT hata ayıklamayı Başlat** ' ı seçin veya **alt** + **F5**tuşuna basın.

## <a name="debug-from-an-app-that-uses-xslt"></a>XSLT kullanan bir uygulamadan hata ayıklama

Bir uygulamada hata ayıklarken XSLT içine adım aktarabilirsiniz. Bir çağrıda **F11** tuşuna bastığınızda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> hata ayıklayıcı XSLT koduna ileredebilir.

> [!NOTE]
> Sınıfından XSLT 'ye Adımlama <xref:System.Xml.Xsl.XslTransform> desteklenmez. <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, hata ayıklama SıRASıNDA XSLT 'de adımlamayı destekleyen tek XSLT işlemcisidir.

### <a name="to-start-debugging-an-xslt-application"></a>XSLT uygulamasında hata ayıklamaya başlamak için

1. Nesnenin örneği oluşturulurken <xref:System.Xml.Xsl.XslCompiledTransform> , `enableDebug` parametresini kodunuzda olarak ayarlayın `true` . Bu, XSLT işlemcisinin kod derlendiğinde hata ayıklama bilgileri oluşturmasını söyler.

1. XSLT koduna geçmek için **F11** tuşuna basın.

   XSLT stil sayfası yeni bir belge penceresine yüklenir ve XSLT hata ayıklayıcısı başlatılır.

   Alternatif olarak, stil sayfasına bir kesme noktası ekleyebilir ve uygulamanızı çalıştırabilirsiniz.

### <a name="example"></a>Örnek

Aşağıda bir C# XSLT programı örneği verilmiştir. XSLT hata ayıklamanın nasıl etkinleştirileceğini gösterir.

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

[XSLT Profiler](../xml-tools/xslt-profiler.md) , ayrıntılı XSLT performans raporları oluşturarak geliştiricilerin XSLT kodundaki performansla ilgili sorunları ölçmesine, değerlendirmesine ve hedeflemesini sağlayan bir araçtır. Daha fazla bilgi için bkz. [XSLT Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Visual Studio hata ayıklayıcısına ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklama temelleri: kesme noktaları](../debugger/using-breakpoints.md)
