---
title: 'Nasıl yapılır: XSLT hata ayıklamayı başlatma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656325"
---
# <a name="how-to-start-debugging-xslt"></a>Nasıl Yapılır: XSLT Hatalarını Ayıklamaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT hata ayıklayıcısı XSLT stil sayfasında veya XSLT uygulamasında hata ayıklamak için kullanılabilir. Hata ayıklarken, kodu Adımlama, Adımlama veya dışarı atlama yoluyla tek seferde bir satırı çalıştırabilirsiniz. Kod Adımlama işlevini kullanma komutları, XSLT hata ayıklayıcısında diğer Visual Studio hata ayıklayıcıları için aynıdır. Hata ayıklamayı başlattığınızda, XSLT hata ayıklayıcı giriş belgesini ve XSLT çıkışını göstermek için Windows 'u açar.

## <a name="xml-editor"></a>XML Düzenleyicisi
 Hata ayıklayıcıyı XML düzenleyicisinden başlatabilirsiniz. Bu, stil sayfasını tasarlarken hata ayıklamanıza olanak sağlar.

#### <a name="to-start-debugging-from-a-style-sheet"></a>Bir stil sayfasından hata ayıklamaya başlamak için

1. XML düzenleyicisinde stil sayfasını açın.

2. **XML** menüsünden **XSL hata ayıkla** ' yı seçin.

#### <a name="to-start-debugging-from-an-xml-input-document"></a>XML giriş belgesinden hata ayıklamayı başlatmak için

1. XML belgesini XML düzenleyicisinde açın.

2. **XML** menüsünden **XSL hata ayıkla** ' yı seçin.

## <a name="xslt-from-other-languages"></a>Diğer dillerden XSLT
 Ayrıca, bir uygulamada hata ayıklarken XSLT 'ye de adım aktarabilirsiniz. Bir çağrıda F11 tuşuna bastığınızda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> hata AYıKLAYıCı XSLT koduna ileredebilir.

> [!NOTE]
> Sınıfından XSLT 'ye Adımlama <xref:System.Xml.Xsl.XslTransform> desteklenmez. <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, hata ayıklama SıRASıNDA XSLT 'de adımlamayı destekleyen tek XSLT işlemcisidir.

#### <a name="to-start-debugging-an-xslt-application"></a>XSLT uygulamasında hata ayıklamaya başlamak için

1. Nesnenin örneği oluşturulurken <xref:System.Xml.Xsl.XslCompiledTransform> , `enableDebug` parametresini kodunuzda olarak ayarlayın `true` .

     Bu, XSLT işlemcisinin kod derlendiğinde hata ayıklama bilgileri oluşturmasını söyler.

2. XSLT koduna geçmek için F11 tuşuna basın.

     XSLT stil sayfası yeni bir belge penceresine yüklenir ve XSLT hata ayıklayıcısı başlatılır.

     Alternatif olarak, stil sayfasına bir kesme noktası ekleyebilir ve uygulamanızı çalıştırabilirsiniz.

### <a name="example"></a>Örnek
 Aşağıda bir C# XSLT programı örneği verilmiştir. XSLT hata ayıklamanın nasıl etkinleştirileceğini gösterir.

```
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) [kodu Adımlama genel bakış](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
