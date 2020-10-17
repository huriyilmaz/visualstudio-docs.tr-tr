---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
description: Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için gelişmiş derleyici ayarları iletişim kutusunu nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0335ee8ef1c385da13c2043ffcfa94c264a5934a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92137044"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)

Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **Advancedcompiler ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

2. **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Derle** sekmesine tıklayın.

3. [Derle sayfasında, proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), **yapılandırma** ve **platformu**seçin. Basitleştirilmiş derleme yapılandırmalarında **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../../debugger/how-to-set-debug-and-release-configurations.md).

4. **Gelişmiş derleme seçenekleri**' ne tıklayın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>İyileştirmeler

Aşağıdaki seçenekler, bir program dosyasını daha küçük hale getirmek, bir programın daha hızlı çalışmasını sağlamak ya da yapı sürecini hızlandırmak için bazı durumlarda en iyileştirmeleri belirler.

**Tamsayı taşma denetimlerini kaldır**

Tam sayı taşma denetimini etkinleştirmek için bu onay kutusu varsayılan olarak temizlenir. Tamsayı taşma denetimini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu seçerseniz, tamsayı hesaplamaları daha hızlı olabilir. Ancak, taşma denetimini ve veri türü kapasitelerinin taşmasını kaldırırsanız hatalı sonuçlar, bir hata oluşmadan depolanabilir.

Taşma koşulları işaretliyse ve bir tamsayı işlemi taşarsa, bir <xref:System.OverflowException> özel durum oluşturulur. Taşma koşulları işaretli değilse, tamsayı işlemi taşma bir özel durum oluşturmaz.

**İyileştirmeleri etkinleştir**

Derleyici iyileştirmelerini devre dışı bırakmak için bu onay kutusu varsayılan olarak temizlenir. Derleyici iyileştirmelerini etkinleştirmek için bu onay kutusunu seçin. Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, iyileştirmeler çıkış dosyasında kodu yeniden düzenlemeye neden olduğundan, derleyici iyileştirmeleri hata ayıklamayı zorlaştırır.

 **DLL taban adresi**

Bu metin kutusu, varsayılan DLL taban adresini onaltılık biçimde görüntüler. Sınıf kitaplığı ve denetim kitaplığı projelerinde, bu metin kutusunu, DLL oluşturulduğunda kullanılacak temel adresi belirtmek için kullanabilirsiniz.

 **Hata ayıklama bilgisi oluştur**

Listeden **hiçbiri**, **tam**veya **pdb** 'yi seçin. **None** hiçbir hata ayıklama bilgisinin üretilmediği belirtir. **Tam** hata ayıklama bilgilerinin oluşturulduğunu ve **PDB** 'nin yalnızca pdb hata ayıklama bilgilerinin oluşturulması gerektiğini belirtir. Bu seçenek için varsayılan değer **Full**değeridir.

## <a name="compilation-constants"></a>Derleme sabitleri

Koşullu derleme sabitleri, tanımlanmış sabitler ortak olduğundan ve projedeki tüm dosyalar için geçerli olması dışında, bir kaynak dosyasında [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) Önişlemci yönergesini kullanmayla benzer bir etkiye sahiptir. Koşullu derleme sabitlerini #If birlikte kullanabilirsiniz [... Sonra... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) yönergesi, kaynak dosyaları koşullu olarak derler. Bkz. [koşullu derleme](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Hata ayıklama sabiti tanımla**

Varsayılan olarak, bu onay kutusu seçilidir ve bir hata ayıklama sabiti ayarlanır.

 **Izleme sabitini tanımlama**

Varsayılan olarak, bu onay kutusu seçilidir ve bir Izleme sabiti ayarlanır.

 **Özel sabitler**

Bu metin kutusuna uygulamanız için özel sabitler girin. Şu biçim kullanılarak girişler virgülle ayrılmalıdır: **name1 = "değer1", AD2 = "değer2", name3 = "Value3"**.

## <a name="other-settings"></a>Diğer ayarlar

**Serileştirme derlemeleri oluştur**

Bu ayar derleyicinin XML serileştirme derlemeleri oluşturup oluşturmayacağını belirtir. <xref:System.Xml.Serialization.XmlSerializer>Kodunuzda türleri seri hale getirmek için bu sınıfı kullandıysanız, serileştirme derlemeleri ' nin başlangıç performansını iyileştirebilir. Bu seçenek için varsayılan değer **Auto**' dır. **Otomatik** serileştirme derlemelerinin yalnızca <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki türleri XML olarak kodlamak için kullandıysanız oluşturulacağını belirtir. **Kapalı** , kodunuzun kullanıp kullanmadığına bakılmaksızın serileştirme derlemelerinin hiçbir şekilde üretilmediğini belirtir <xref:System.Xml.Serialization.XmlSerializer> . **On** , serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme bütünleştirilmiş kodları.XmlSerializers.dll olarak adlandırılır `TypeName` .

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
