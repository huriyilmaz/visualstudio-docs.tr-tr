---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ebc2da5e71dbdee13df4cf658f3681804879f58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596937"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)

Projenin gelişmiş yapı yapılandırma özelliklerini belirtmek için **Project Designer'ın** **AdvancedCompiler Ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projeleri için geçerlidir.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin.

2. **Proje** menüsünde **Özellikler'i**tıklatın. Proje **Tasarımcısı** göründüğünde, **Derle** sekmesini tıklatın.

3. [Derle Sayfasında, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), **Yapılandırma** ve **Platform**seçin. Basitleştirilmiş yapı yapılandırmalarında **Yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için [bkz: Hata ayıklama ve sürüm yapılandırmaları ayarlayın.](../../debugger/how-to-set-debug-and-release-configurations.md)

4. **Gelişmiş Derleme Seçenekleri'ni**tıklatın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>İyileştirmeler

Aşağıdaki seçenekler, bazı durumlarda bir program dosyasını küçültmeye, programın daha hızlı çalışmasını sağlayacak veya yapı işlemini hızlandırabilecek optimizasyonları belirtir.

**Tümesi taşması denetimlerini kaldırma**

Bu onay kutusu, tamsayı taşması denetimini etkinleştirmek için varsayılan olarak temizlenir. Tamsayı taşma denetimini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu seçerseniz, tamsayı hesaplamaları daha hızlı olabilir. Ancak, taşma denetimini ve veri türü kapasitelerinin taşmasını kaldırırsanız, yanlış sonuçlar yükseltilmeden depolanabilir.

Taşma koşulları denetlenir ve bir bir insa <xref:System.OverflowException> işlemi taşarsa, bir özel durum atılır. Taşma koşulları denetlenmezse, tümseci işlemi taşmaları özel bir durum oluşturur.

**Optimizasyonları etkinleştirme**

Bu onay kutusu, varsayılan olarak derleyici optimizasyonlarını devre dışı bırakmak için temizlenir. Derleyici optimizasyonlarını etkinleştirmek için bu onay kutusunu seçin. Derleyici optimizasyonları çıktı dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, optimizasyonlar çıktı dosyasında kod yeniden düzenlenmesine neden olduğundan, derleyici optimizasyonları hata ayıklama zor laştırabilir.

 **DLL taban adresi**

Bu metin kutusu hexadecimal biçiminde varsayılan DLL temel adresini görüntüler. Sınıf Kitaplığı ve Denetim Kitaplığı projelerinde, DLL oluşturulduğunda kullanılacak temel adresi belirtmek için bu metin kutusunu kullanabilirsiniz.

 **Hata ayıklama bilgileri oluşturma**

Listeden **Yok**, **Tam**veya **yalnızca pdb'yi** seçin. **Hiçbiri** hata ayıklama bilgisi oluşturulmaz belirtmezse. **Tam,** tam hata ayıklama bilgilerinin oluşturulup oluşturulacagerektiğini belirtir ve **yalnızca PDB** hata ayıklama bilgilerinin oluşturulması gerektiğini belirtir. Bu seçeneğin varsayılan **Full**değeri Tam'dır.

## <a name="compilation-constants"></a>Derleme Sabitleri

Koşullu derleme sabitleri, tanımlanan sabitlerin herkese açık olması ve projedeki tüm dosyalara uygulanması dışında, kaynak dosyada [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) önişlemci yönergesi kullanma nın etkisine benzer bir etkiye sahiptir. Koşullu derleme sabitlerini #If ile birlikte [kullanabilirsiniz... Sonra ... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) yönergesi koşullu kaynak dosyaları derlemek için. Bkz. [Koşullu Derleme](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **HATA hata sabitini tanımla**

Varsayılan olarak, bu onay kutusu, bir HATA Ayıklama sabitinin ayarlanması belirtilirken seçilir.

 **TRACE sabitini tanımla**

Varsayılan olarak, bu onay kutusu seçilir ve trace sabitinin ayarlanaaçıklanır.

 **Özel sabitler**

Bu metin kutusuna uygulamanız için özel sabitler girin. Girişler bu formu kullanarak virgülle sınırlandırılmalıdır: **Name1="Value1",Name2="Value2",Name3="Value3"**.

## <a name="other-settings"></a>Diğer Ayarlar

**Serileştirme derlemeleri oluşturma**

Bu ayar, derleyicinin XML serileştirme derlemeleri oluşturup oluşturmayacağını belirtir. Serileştirme derlemeleri, bu sınıfı <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki türleri serihale getirmek için kullandıysanız başlangıç performansını artırabilir. Bu seçeneğin varsayılan **Auto**değeri Otomatik'tir. **Otomatik** olarak, serileştirme derlemelerinin yalnızca kodunuzdaki <xref:System.Xml.Serialization.XmlSerializer> türleri XML'e kodlamak için kullandıysanız oluşturulacak ları belirtir. **Kapalı,** kodunuzu kullanıp kullanmadığına <xref:System.Xml.Serialization.XmlSerializer>bakılmaksızın serileştirme derlemelerinin asla oluşturulmayacağını belirtir. **Serileştirme** derlemeleri her zaman oluşturulur belirtir. Serileştirme derlemeleri `TypeName`adı verilir. XmlSerializers.dll.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
