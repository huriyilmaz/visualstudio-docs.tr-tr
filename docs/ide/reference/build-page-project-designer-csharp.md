---
title: Derleme Sayfası, Proje Tasarımcısı (C#)
description: Projenin derleme yapılandırma özelliklerini belirtmek için Project Tasarımcısı'nın Visual Studio sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7892822995b74665ec014530207e565b2c70f78adfc92fab01ad8ac6a97633a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400315"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)

Projenin **derleme** yapılandırma özelliklerini **belirtmek Project Tasarımcısı'nın** Derleme sayfasını kullanın. Bu sayfa yalnızca projeler [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] için geçerlidir.

Derleme sayfasına **erişmek için,** içinde bir proje düğümü **(Çözüm** düğümü değil) **Çözüm Gezgini.** Ardından menüde **Görünüm**, **Özellik Sayfaları'ı** seçin. Project Tasarımcısı görüntülendiğinde, Derleme **sekmesini** seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki seçenekler, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmaları ile proje sistemi hata ayıklama veya yayın sürümü derlemeyi belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için, [bkz. How to: Set debug and release configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntü veya değiştirmesi gerektir olduğunu belirtir. Ayarlar Etkin **(Hata Ayıklama) (varsayılan ayardır),** Hata **Ayıklama,** Sürüm veya Tüm **Yapılandırmalar olabilir.**

**Platform**

Hangi platform ayarlarının görüntü veya değiştirmesi gerektir olduğunu belirtir. Varsayılan ayar Etkin **(Herhangi bir CPU) ayarıdır.** etkin platformu değiştirmek için **Yapılandırma Yöneticisi.** Daha fazla bilgi için, [bkz. How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Genel

Aşağıdaki seçenekler çeşitli C# derleyici ayarlarını yapılandırmaya olanak sağlar.

**Koşullu derleme sembolleri**

Koşullu derlemenin hangi sembolleri gerçekleştireceklerini belirtir. Simgeleri noktalı virgül (";") ile ayırabilirsiniz. Daha fazla bilgi için bkz. [/define (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**DEBUG sabiti tanımlama**

Uygulamanıza tüm kaynak kodu dosyalarında bir sembol olarak DEBUG tanımlar. Bunu seçmek, komut satırı seçeneğini `/define:DEBUG` kullanmaya eşdeğerdir.

**TRACE sabiti tanımlama**

TRACE'i uygulamandaki tüm kaynak kod dosyalarında sembol olarak tanımlar. Bunu seçmek, komut satırı seçeneğini `/define:TRACE` kullanmaya eşdeğerdir.

**Platform Hedefi**

Çıkış dosyası tarafından hedeflen işlemciyi belirtir. Herhangi bir 32 bit Intel uyumlu işlemci için **x86'yi** seçin, 64 bit Intel uyumlu işlemciler için **x64'ü** seçin, ARM işlemciler için **ARM'yi** seçin veya herhangi bir işlemcinin kabul edilebilir olduğunu belirtmek için **Herhangi bir CPU'yu** seçin. **Herhangi bir CPU,** uygulamanın en geniş donanım aralığında çalışmasına izin veren projeler için varsayılan değerdir.

Daha fazla bilgi için bkz. [/platform (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Nullable**

Proje genelinde null değere sahip C# bağlamını belirtir. Bu kullanıcı arabirimi seçeneği Visual Studio 16.5'te tanıtıldı ve yalnızca C# 8.0 veya sonraki bir kullanan projeler için etkinleştirildi.

Daha fazla bilgi için bkz. [Boş Değer Değiştirilebilir Bağlamlar.](/dotnet/csharp/nullable-references#nullable-contexts)

**32 bit tercih**

**Prefer32-bit** onay kutusu seçiliyse, uygulama hem 32 bit hem de 64 bit uygulamanın 32 bitlik sürümlerinde 32 bitlik bir uygulama Windows. Onay kutusu temizli ise uygulama, Windows'ın 32 bit sürümlerinde 32 bit uygulama olarak ve uygulamanın 64 bit sürümlerinde 64 bit uygulama olarak Windows.

Bir uygulamayı 64 bit uygulama olarak çalıştırıyorsanız, işaretçi boyutu iki katına çıkar ve yalnızca 32 bit olan diğer kitaplıklarda uyumluluk sorunları oluşabilir. Yalnızca 4 GB'den fazla belleğe veya 64 bit yönergelere ihtiyacı varsa 64 bitlik bir uygulama çalıştırmak önemli bir performans geliştirmesi sağlar.

Bu onay kutusu yalnızca aşağıdaki koşulların hepsi doğruysa kullanılabilir:

- Derleme **Sayfasında Platform** hedef **listesi Herhangi bir** CPU olarak **ayarlanır.**

- Uygulama **Sayfasında,** Çıkış **türü listesi** projenin bir uygulama olduğunu belirtir.

- Uygulama **Sayfasında,** Hedef **çerçeve listesi** 4.5 .NET Framework belirtir.

**Güvenli olmayan koda izin ver**

Derlemek için güvenli olmayan anahtar [sözcüğünü kullanan](/dotnet/csharp/language-reference/keywords/unsafe) koda izin verir. Daha fazla bilgi için [bkz. /unsafe (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Kodu iyileştirme**

Çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmesi için derleyici tarafından gerçekleştirilen iyileştirmeleri etkinleştirin veya devre dışı gerçekleştirilir. Daha fazla bilgi için bkz. [/optimize (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar

Derleme işleminin hata ve uyarı seçeneklerini yapılandırmak için aşağıdaki ayarlar kullanılır.

**Uyarı düzeyi**

Derleyici uyarıları için görüntülenme düzeyini belirtir. Daha fazla bilgi için [bkz. /warn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Uyarıları gizleme**

Derleyicinin bir veya daha fazla uyarı oluşturma becerisini engeller. Birden çok uyarı numaralarını virgül veya noktalı virgülle ayırın. Daha fazla bilgi için bkz. [/nowarn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Uyarıları Hata Olarak Davran

Aşağıdaki ayarlar, hangi uyarıların hata olarak kabul edilir olduğunu belirtmek için kullanılır. Derleme bir uyarıyla karşılaştığında hangi koşulların hata döndürür? altında belirtmek için aşağıdaki seçeneklerden birini belirleyin. Daha fazla bilgi için bkz. [/warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Hiçbiri** - Uyarılara hata olarak davranmaz.

**All** - Tüm uyarıları hata olarak davranır.

**Belirli uyarılar** - Belirtilen uyarıları hata olarak davranır. Birden çok uyarı numaralarını virgül veya noktalı virgülle ayırın.

> [!TIP]
> Kod analizi uyarılarının hata olarak kabul edilebilir olması istemiyorsanız bkz. Kod analizi hakkında [SSS.](/visualstudio/code-quality/analyzers-faq#treat-warnings-as-errors)

## <a name="output"></a>Çıktı

Derleme işleminin çıkış seçeneklerini yapılandırmak için aşağıdaki ayarlar kullanılır.

**Çıkış yolu**

Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Bu kutuya derleme çıkışının yolunu girin veya gözat **düğmesini seçerek** bir yol belirtin. Yol görelidir; Mutlak bir yol girersiniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug veya bin\Release \\ yoludur.

Basitleştirilmiş derleme yapılandırmaları ile proje sistemi hata ayıklama veya yayın sürümü derlemeyi belirler. Hata **Ayıklama** **menüsündeki** (F5) Build komutu, belirttiğiniz Çıkış yolundan bağımsız olarak derlemeyi hata **ayıklama konuma** koyacak. Ancak, **Derleme** menüsündeki **Build** komutu bunu belirttiğiniz konuma koyar. Daha fazla bilgi için bkz. [Derleme Yapılandırmalarını Anlama.](../../ide/understanding-build-configurations.md)

**XML belge dosyası**

Belge açıklamalarının işlenecek dosyanın adını belirtir. Daha fazla bilgi için [bkz. /doc (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**COM birlikte çalışma için kaydolma**

Yönetilen uygulamanıza com nesnesinin yönetilen uygulamayla etkileşim kurmasını sağlayan bir COM nesnesini (COM çağrılabilir sarmalayıcı) ortaya çıkartır. COM **birlikte** çalışma [](../../ide/reference/application-page-project-designer-visual-basic.md) özelliğine kaydolma özelliğinin kullanılabilir olması için, bu  uygulama için **Project Tasarımcısı'nın** Uygulama sayfasındaki Çıkış türü özelliği Sınıf Kitaplığı **olarak** ayarlanır. Uygulamanıza dahil olabileceğiniz ve BIR COM nesnesi olarak açığa çıkarabilirsiniz örnek bir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sınıf için [bkz. Örnek COM Sınıfı.](/dotnet/csharp/programming-guide/interop/example-com-class)

**Serileştirme derlemesi oluşturma**

Derleyicinin XML serileştirme derlemeleri oluşturmak için XML Serileştiricisi Oluşturma Aracı (Sgen.exe) kullanıp kullanmayacaklarını belirtir. Serileştirme derlemeleri, kodundaki türleri <xref:System.Xml.Serialization.XmlSerializer> serileştirmek için bu sınıfı kullandıysanız başlatma performansını geliştirebilir. Varsayılan olarak, bu seçenek Otomatik olarak ayarlanır ve bu, serileştirme derlemelerinin yalnızca kodundaki türleri XML'ye kodlamak için kullandıysanız <xref:System.Xml.Serialization.XmlSerializer> oluşturul olacağını belirtir. **Kapalı,** kodunuzun kullandığına bakılmaksızın serileştirme derlemelerinin hiçbir zaman oluşturulamay olmadığını <xref:System.Xml.Serialization.XmlSerializer> belirtir. **üzerinde,** serileştirme derlemelerinin her zaman oluşturul olacağını belirtir. Serileştirme derlemeleri, `TypeName`.XmlSerializers.dll. Daha fazla bilgi için [bkz. XML Serileştiricisi Oluşturma Aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Gelişmiş**

Gelişmiş Derleme Oluşturma İletişim [Ayarlar (C#) iletişim kutusunu görüntülemek](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) için tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
