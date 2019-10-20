---
title: Gelişmiş derleyici ayarları Iletişim kutusu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba666b0ff5544b185f82a66c78d6259e9f1268fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651763"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **Advancedcompiler ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir.

### <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

2. **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Derle** sekmesine tıklayın.

3. [Derle sayfasında, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), **yapılandırma** ve **platformu**seçin. Basitleştirilmiş derleme yapılandırmalarında **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

4. **Gelişmiş derleme seçenekleri**' ne tıklayın.

   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="optimizations"></a>İyileştirmeleri
 Aşağıdaki seçenekler, bir program dosyasını daha küçük hale getirmek, bir programın daha hızlı çalışmasını sağlamak ya da yapı sürecini hızlandırmak için bazı durumlarda en iyileştirmeleri belirler.

 **Tamsayı taşma denetimlerini kaldır** Varsayılan olarak, bu onay kutusu, tamsayı taşma denetimini etkinleştirmek için temizlenir. Tamsayı taşma denetimini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu seçerseniz, tamsayı hesaplamaları daha hızlı olabilir. Ancak, taşma denetimini ve veri türü kapasitelerinin taşmasını kaldırırsanız hatalı sonuçlar, bir hata oluşmadan depolanabilir.

 Taşma koşulları işaretliyse ve bir tamsayı işlemi taşarsa bir <xref:System.OverflowException> özel durumu oluşturulur. Taşma koşulları işaretli değilse, tamsayı işlemi taşan bir özel durum oluşturmaz.

 **Iyileştirmeleri etkinleştir** Bu onay kutusu varsayılan olarak, derleyici iyileştirmelerini devre dışı bırakmak için temizlenir. Derleyici iyileştirmelerini etkinleştirmek için bu onay kutusunu seçin. Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, iyileştirmeler çıkış dosyasında kodu yeniden düzenlemeye neden olduğundan, derleyici iyileştirmeleri hata ayıklamayı zorlaştırır.

 **Dll taban adresi** Bu metin kutusu, varsayılan DLL taban adresini onaltılık biçimde görüntüler. Sınıf kitaplığı ve denetim kitaplığı projelerinde, bu metin kutusunu, DLL oluşturulduğunda kullanılacak temel adresi belirtmek için kullanabilirsiniz.

 **Hata ayıklama bilgisi oluştur** Listeden **hiçbiri**, **tam**veya **pdb** 'yi seçin. **None** hiçbir hata ayıklama bilgisinin üretilmediği belirtir. **Tam** hata ayıklama bilgilerinin oluşturulduğunu ve **PDB** 'nin yalnızca pdb hata ayıklama bilgilerinin oluşturulacağını belirtir. Varsayılan olarak, bu seçenek **Full**olarak ayarlanır.

## <a name="compilation-constants"></a>Derleme sabitleri
 Koşullu derleme sabitleri, tanımlanmış sabitler ortak olduğundan ve projedeki tüm dosyalar için geçerli olması dışında, bir kaynak dosyasında [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) Önişlemci yönergesini kullanmayla benzer bir etkiye sahiptir. Koşullu derleme sabitlerini #If birlikte kullanabilirsiniz [... Sonra... #Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) yönergesi, kaynak dosyaları koşullu olarak derler. Bkz. [koşullu derleme](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).

 **Hata ayıklama sabiti tanımla** Varsayılan olarak, bu onay kutusu seçilidir ve bir hata ayıklama sabiti ayarlanır.

 **İzleme sabitini tanımlama** Varsayılan olarak, bu onay kutusu seçilidir ve bir Izleme sabiti ayarlanır.

 **Özel sabitler** Bu metin kutusuna uygulamanız için özel sabitler girin. Şu biçim kullanılarak girişler virgülle ayrılmalıdır: **name1 = "değer1", AD2 = "değer2", name3 = "Value3"** .

## <a name="other-settings"></a>Diğer ayarlar
 **Serileştirme derlemeleri oluştur** Bu ayar derleyicinin XML serileştirme derlemeleri oluşturup oluşturmayacağını belirtir. Kodunuzda türleri seri hale getirmek için bu sınıfı kullandıysanız, serileştirme derlemeleri <xref:System.Xml.Serialization.XmlSerializer> başlangıç performansını iyileştirebilir. Varsayılan olarak, bu seçenek **Auto**olarak ayarlanır, bu da serileştirme derlemelerinin yalnızca KODUNUZDA türleri XML olarak kodlamak için <xref:System.Xml.Serialization.XmlSerializer> kullandıysanız oluşturulacağını belirtir. **Kapalı** , kodunuzun <xref:System.Xml.Serialization.XmlSerializer> kullanıp kullanmadığına bakılmaksızın serileştirme derlemelerinin hiçbir şekilde üretilmediğini belirtir. **On** , serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme bütünleştirilmiş kodları `TypeName`. Xmlserileştiriciler. dll olarak adlandırılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
