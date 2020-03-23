---
title: Derleme Sayfası, Proje Tasarımcısı (C#)
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf50c653d82a7de22d5a81fd81c38db0db1be8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76923262"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)

Projenin **yapı** yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı'nın** Yapı sayfasını kullanın. Bu sayfa yalnızca [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeler için geçerlidir.

**Yapı** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin. Ardından menüde **Görünüm**, **Özellik Sayfaları'nı** seçin. Proje Tasarımcısı **göründüğünde, Yapı** sekmesini seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki seçenekler, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak tanır.

> [!NOTE]
> Basitleştirilmiş yapı yapılandırmalarıyla, proje sistemi hata ayıklama mı yoksa sürüm sürümü mü oluşturup oluşturmayacağını belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için [bkz: Hata ayıklama ve sürüm yapılandırmaları ayarlayın.](../../debugger/how-to-set-debug-and-release-configurations.md)

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntülenecin veya değiştirilen leri belirtir. Ayarlar Etkin **(Hata Ayıklama)** (bu varsayılan), **Hata Ayıklama**, **Release**veya **Tüm Yapılandırmaları**olabilir.

**Platform**

Hangi platform ayarlarının görüntüleneceğin veya değiştirilen leri belirtir. Varsayılan ayar **Etkin (Herhangi bir CPU)** olduğunu. **Configuration Manager'ı**kullanarak etkin platformu değiştirebilirsiniz. Daha fazla bilgi için [bkz: Yapılandırmalar oluştur ve düzenleme.](../../ide/how-to-create-and-edit-configurations.md)

## <a name="general"></a>Genel

Aşağıdaki seçenekler, birkaç C# derleyici ayarını yapılandırmanızı sağlar.

**Koşullu derleme sembolleri**

Koşullu derlemenin gerçekleştirilmeye yönelik sembolleri belirtir. Yarı-iki nokta lı ayrı semboller (";"). Daha fazla bilgi için bkz: [/define (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**HATA hata sabitini tanımla**

HATA Hata Ayıklama'yı uygulamanızdaki tüm kaynak kodu dosyalarında bir sembol olarak tanımlar. Bunu `/define:DEBUG` seçmek, komut satırı seçeneğini kullanmaya eşdeğerdir.

**TRACE sabitini tanımla**

TRACE'i uygulamanızdaki tüm kaynak kod dosyalarında bir sembol olarak tanımlar. Bunu `/define:TRACE` seçmek, komut satırı seçeneğini kullanmaya eşdeğerdir.

**Platform Hedefi**

İşlemcinin çıktı dosyası tarafından hedef alınmasını belirtir. Herhangi bir 32-bit Intel uyumlu işlemci için **x86** seçin, herhangi bir 64-bit Intel uyumlu işlemci için **x64** seçin, ARM işlemciler için **ARM** seçin veya herhangi bir işlemci kabul edilebilir olduğunu belirtmek için **Herhangi bir CPU** seçin. **Herhangi bir CPU,** uygulamanın en geniş donanım aralığında çalışmasına izin verdiğinden, projeler için varsayılan değerdir.

Daha fazla bilgi için bkz: [/platform (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Null Atanabilir**

Proje genelindeki C# nullable bağlamını belirtir. Bu UI seçeneği Visual Studio 16.5'te tanıtıldı ve yalnızca C# 8.0 veya sonraki projeleri kullanan projeler için etkinleştirildi.

Daha fazla bilgi için [Nullable Contexts'a](/dotnet/csharp/nullable-references#nullable-contexts)bakın.

**32 bit tercih etmeyi tercih edin**

**Prefer32-bit** onay kutusu seçilirse, uygulama Windows'un hem 32 bit hem de 64 bit sürümlerinde 32 bit uygulama olarak çalışır. Onay kutusu temizlenirse, uygulama Windows'un 32 bit sürümlerinde 32 bit uygulama ve Windows'un 64 bit sürümlerinde 64 bit uygulama olarak çalışır.

Bir uygulamayı 64 bit uygulama olarak çalıştırırsanız, işaretçi boyutu iki katına çıkar ve yalnızca 32 bit olan diğer kitaplıklarla uyumluluk sorunları oluşabilir. 64 bit bir uygulamayı yalnızca 4 GB'tan fazla belleğe veya 64 bit yönergelere ihtiyaç duyduğunda çalıştırmak yararlıdır.

Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa kullanılabilir:

- Yapı **Sayfasında,** **Platform hedef** listesi Herhangi **bir CPU**olarak ayarlanır.

- Uygulama **Sayfasında,** **Çıktı türü** listesi projenin bir uygulama olduğunu belirtir.

- Uygulama **Sayfasında**, **Hedef çerçeve** listesi .NET Framework 4.5'i belirtir.

**Güvenli olmayan koda izin ver**

Derlemek için [güvenli olmayan](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğü kullanan koda izin verir. Daha fazla bilgi için bkz: [/güvensiz (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Kodu optimize edin**

Çıktı dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen optimizasyonları etkinleştirin veya devre dışı edin. Daha fazla bilgi için bkz: [/optimize (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar

Yapı işlemi için hata ve uyarı seçeneklerini yapılandırmak için aşağıdaki ayarlar kullanılır.

**Uyarı düzeyi**

Derleyici uyarıları için görüntülenecek düzeyi belirtir. Daha fazla bilgi için bkz/ [/warn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Uyarıları bastırma**

Derleyicinin bir veya daha fazla uyarı oluşturma yeteneğini engeller. Birden çok uyarı sayısını virgül veya yarı kolon ile ayırın. Daha fazla bilgi için bkz: [/nowarn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Uyarıları Hata Olarak Değerlendirin

Hangi uyarıların hata olarak kabul edilir belirtmek için aşağıdaki ayarlar kullanılır. Yapı bir uyarıyla karşılaştığında hatanın hangi koşullarda döndürülecek lerini belirtmek için aşağıdaki seçeneklerden birini seçin. Daha fazla bilgi için bkz: [/warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Yok** - Hiçbir uyarıyı hata olarak ele almaz.

**Tüm** - Tüm uyarıları hata olarak ele alar.

**Belirli uyarılar** - Belirtilen uyarıları hata olarak ele alalım. Birden çok uyarı sayısını virgül veya yarı kolon ile ayırın.

> [!TIP]
> Kod çözümleme uyarılarının hata olarak ele alınmasını istemiyorsanız, [Kod çözümlemesi SSS'ye](../../code-quality/analyzers-faq.md#treat-warnings-as-errors)bakın.

## <a name="output"></a>Çıktı

Yapı işlemi için çıktı seçeneklerini yapılandırmak için aşağıdaki ayarlar kullanılır.

**Çıkış yolu**

Bu projenin yapılandırması için çıktı dosyalarının konumunu belirtir. Bu kutuya yapı çıktısının yolunu girin veya bir yol belirtmek için **Gözat** düğmesini seçin. Yol görecelidir; mutlak bir yol girerseniz, göreceli olarak kaydedilir. Varsayılan yol bin\Debug veya bin\Release'\\tir.

Basitleştirilmiş yapı yapılandırmalarıyla, proje sistemi hata ayıklama mı yoksa sürüm sürümü mü oluşturup oluşturmayacağını belirler. **Hata Ayıklama** menüsünden (F5) **Yapı** komutu, belirttiğiniz **Çıktı yolundan** bağımsız olarak yapıyı hata ayıklama konumuna koyar. Ancak, **Yapı** menüsünden **Yap** komutu, onu belirttiğiniz konuma koyar. Daha fazla bilgi için [bkz.](../../ide/understanding-build-configurations.md)

**XML dokümantasyon dosyası**

Belge leme yorumlarının işlenecek dosyanın adını belirtir. Daha fazla bilgi için bkz: [/doc (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**COM interop'a kaydolun**

Yönetilen uygulamanızın, com nesnesi tarafından yönetilen uygulamanızla etkileşime geçmesine izin veren bir COM nesnesini (COM çağrılabilir sarıcı) ortaya çıkaracağını gösterir. Bu uygulama için **Proje Tasarımcısı'nın** [Uygulama sayfasındaki](../../ide/reference/application-page-project-designer-visual-basic.md) **Çıktı türü** özelliğinin, **COM interop özelliğinin** kullanılabilmesi için **Sınıf Kitaplığı** olarak ayarlanmalıdır. Uygulamanıza [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ekleyebileceğiniz ve COM nesnesi olarak ortaya çıkarabileceğiniz örnek bir sınıf için [Bkz. Örnek COM Sınıfı.](/dotnet/csharp/programming-guide/interop/example-com-class)

**Serileştirme derlemesi oluşturma**

Derleyicinin XML serileştirme derlemeleri oluşturmak için XML Serializer Generator Tool'u (Sgen.exe) kullanıp kullanmayacağını belirtir. Serileştirme derlemeleri, bu sınıfı <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki türleri serihale getirmek için kullandıysanız başlangıç performansını artırabilir. Varsayılan olarak, bu **seçenek,** serileştirme derlemelerinin yalnızca kodunuzdaKi türleri XML'e kodlamak için kullandıysanız <xref:System.Xml.Serialization.XmlSerializer> oluşturulmasını belirten Otomatik olarak ayarlanır. **Kapalı,** kodunuzu kullanıp kullanmadığına <xref:System.Xml.Serialization.XmlSerializer>bakılmaksızın serileştirme derlemelerinin asla oluşturulmayacağını belirtir. **Serileştirme** derlemeleri her zaman oluşturulur belirtir. Serileştirme derlemeleri `TypeName`adı verilir. XmlSerializers.dll. Daha fazla bilgi için [Bkz. XML Serializer Jeneratör Aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Gelişmiş**

Gelişmiş Yapı [Ayarları İletişim Kutusu (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) iletişim kutusunu görüntülemek için tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
