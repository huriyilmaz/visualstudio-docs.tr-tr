---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)
description: Projenin gelişmiş derleme yapılandırma özelliklerini belirtmek için Ayarlar Derleyici Yapılandırması iletişim kutusunu kullanmayı öğrenin.
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
ms.openlocfilehash: 92eceec6d7c7c5194b3cf0322c8e6b1253e1cee82a77dce84976e8500d936376
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387635"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)

Projenin gelişmiş derleme Ayarlar belirtmek için Project **Tasarımcısı'nın** **AdvancedCompiler** Ayarlar iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic için geçerlidir.

## <a name="to-access-this-dialog-box"></a>Bu iletişim kutusuna erişmek için

1. Bu **Çözüm Gezgini** proje düğümünü (Çözüm düğümü **değil)** seçin.

2. Yeni **Project** Özellikler'e **tıklayın.** Project **Tasarımcısı göründüğünde** Derle **sekmesine** tıklayın.

3. Derleme [Sayfasında, Project Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)seçeneğini ve Yapılandırma **ve Platform'ı** **seçin.** Basitleştirilmiş derleme **yapılandırmalarında Yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için, [bkz. How to: Set debug and release configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Gelişmiş **Derleme Seçenekleri'ne tıklayın.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>İyileştirmeler

Aşağıdaki seçenekler, bazı durumlarda bir program dosyasını daha küçük hale getirme, bir programın daha hızlı çalışması veya derleme işlemini hızlandıran iyileştirmeleri belirtir.

**Tamsayı taşma denetimlerini kaldırma**

Bu onay kutusu, tamsayı taşma denetimine olanak sağlamak için varsayılan olarak temizdir. Tamsayı taşma işaretlerini kaldırmak için bu onay kutusunu seçin. Bu onay kutusunu işaret edersanız tamsayı hesaplamaları daha hızlı olabilir. Öte yandan taşma denetimlerini ve veri türü kapasite taşmalarını kaldırırsanız, yanlış sonuçlar hataya neden olmadan depolanmış olabilir.

Taşma koşulları denetlenir ve tamsayı işlemi taşması olursa <xref:System.OverflowException> bir özel durum oluşturur. Taşma koşulları denetlenmezse tamsayı işlemi taşmaları bir özel durum oluşturur.

**İyileştirmeleri etkinleştirme**

Derleyici iyileştirmelerini devre dışı bırakmak için bu onay kutusu varsayılan olarak temizlenmiş durumdadır. Derleyici iyileştirmelerini etkinleştirmek için bu onay kutusunu seçin. Derleyici iyileştirmeleri çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirir. Ancak, iyileştirmeler çıkış dosyasında kod yeniden düzenlemeye neden olduğundan, derleyici iyileştirmeleri hata ayıklamayı zorlaştırabilir.

 **DLL temel adresi**

Bu metin kutusu varsayılan DLL temel adresini onaltılık biçimde görüntüler. Sınıf Kitaplığı ve Denetim Kitaplığı projelerinde, DLL oluşturulduğunda kullanılacak temel adresi belirtmek için bu metin kutusunu kullanabilirsiniz.

 **Hata ayıklama bilgileri oluşturma**

Listeden **Hiçbiri,** **Tam** veya **yalnızca pdb'yi** seçin. **Hiçbiri,** hata ayıklama bilgisi oluşturula olmadığını belirtir. **Tam,** tam hata ayıklama bilgileri oluşturul olacağını belirtir ve **yalnızca pdb-only,** yalnızca PDB hata ayıklama bilgileri oluşturul gerektiğini belirtir. Bu seçenek için varsayılan değer **Tam'dır.**

## <a name="compilation-constants"></a>Derleme Sabitleri

Koşullu derleme sabitleri, bir kaynak dosyada [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) önişlemci yönergesi kullanmaya benzer, ancak tanımlanan sabitler ortaktır ve proje üzerindeki tüm dosyalara uygulanır. Koşullu derleme sabitlerini [#If... Ardından... #Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) dosyaları koşullu olarak derlemek için yönergeyi kullanın. Bkz. [Koşullu Derleme.](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)

 **DEBUG sabiti tanımlama**

Varsayılan olarak bu onay kutusu seçilidir ve hata ayıklama sabiti ayarlanır.

 **TRACE sabiti tanımlama**

Varsayılan olarak bu onay kutusu seçilidir ve bir TRACE sabiti ayarlanır.

 **Özel sabitler**

Bu metin kutusuna uygulamanıza özel sabitleri girin. Girdiler virgülle sınırlandırılmış olmalı ve şu biçim kullanılarak sınırlandırılmış olması gerekir: **Name1="Value1",Name2="Value2",Name3="Value3"**.

## <a name="other-settings"></a>Diğer Ayarlar

**Serileştirme derlemeleri oluşturma**

Bu ayar, derleyicinin XML serileştirme derlemeleri oluşturıp oluşturmayacaklarını belirtir. Serileştirme derlemeleri, kodundaki türleri serileştirmek için bu sınıfı <xref:System.Xml.Serialization.XmlSerializer> kullandıysanız başlatma performansını geliştirebilir. Bu seçenek için varsayılan değer **Otomatik'tir.** **Serileştirme** derlemelerinin yalnızca kodundaki türleri XML'ye kodlamak için kullandıysanız <xref:System.Xml.Serialization.XmlSerializer> oluşturulabilecekleri otomatik olarak belirtir. **Kapalı,** kodunuzun kullandığına bakılmaksızın serileştirme derlemelerinin hiçbir zaman oluşturulamay olmadığını <xref:System.Xml.Serialization.XmlSerializer> belirtir. **üzerinde,** serileştirme derlemelerinin her zaman oluşturul olacağını belirtir. Serileştirme derlemeleri, `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
