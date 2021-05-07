---
title: Derleme Sayfası, Proje Tasarımcısı (C#)
description: Projenin derleme yapılandırma özelliklerini belirtmek için Visual Studio Proje Tasarımcısı'nın Derleme sayfasını kullanmayı öğrenin.
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
ms.openlocfilehash: 91b254f4c075693e23d8f650356cd97e86a4c746
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798563"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)

Projenin **derleme** yapılandırma özelliklerini **belirtmek için Proje** Tasarımcısı'nın Derleme sayfasını kullanın. Bu sayfa yalnızca projeler [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] için geçerlidir.

Derleme sayfasına **erişmek için,** içinde bir proje düğümü **(Çözüm düğümü** değil) **Çözüm Gezgini.** Ardından menüde **Görünüm**, **Özellik Sayfaları'ı** seçin. Proje Tasarımcısı görüntülendiğinde Derleme **sekmesini** seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki seçenekler, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmaları ile proje sistemi bir hata ayıklama veya yayın sürümü derlemeyi belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için, [bkz. How to: Set debug and release configurations](../../debugger/how-to-set-debug-and-release-configurations.md).

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntü veya değiştirmesi gerektir olduğunu belirtir. Ayarlar Etkin **(Hata Ayıklama) (varsayılan ayardır),** Hata **Ayıklama,** Sürüm veya Tüm **Yapılandırmalar olabilir.**

**Platform**

Hangi platform ayarlarının görüntüle veya değiştir yapılandırılamayacaklarını belirtir. Varsayılan ayar Etkin **(Herhangi bir CPU) ayarıdır.** etkin platformu değiştirmek için **Yapılandırma Yöneticisi.** Daha fazla bilgi için, [bkz. How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Genel

Aşağıdaki seçenekler çeşitli C# derleyici ayarlarını yapılandırmaya olanak sağlar.

**Koşullu derleme sembolleri**

Koşullu derlemenin hangi sembolleri gerçekleştireceklerini belirtir. Sembolleri noktalı virgül (";") ile ayırın. Daha fazla bilgi için bkz. [/define (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**Hata ayıklama sabiti tanımla**

Uygulamanızdaki tüm kaynak kodu dosyalarında bir sembol olarak hata ayıklamayı tanımlar. Bunu seçmek, `/define:DEBUG` komut satırı seçeneğini kullanmaya eşdeğerdir.

**Izleme sabitini tanımlama**

Uygulamanızı uygulamanızdaki tüm kaynak kodu dosyalarında sembol olarak tanımlar. Bunu seçmek, `/define:TRACE` komut satırı seçeneğini kullanmaya eşdeğerdir.

**Platform hedefi**

Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** seçeneğini belirleyin, her 64 bit Intel uyumlu işlemci için **x64** seçeneğini belirleyin, ARM işlemcileri için **ARM** 'yi seçin ya da herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** seçin. **Tüm CPU** , uygulamanın en geniş donanım yelpazesi üzerinde çalışmasına izin verdiğinden projeler için varsayılan değerdir.

Daha fazla bilgi için bkz. [/Platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**Yapılamaz**

Proje genelindeki C# Nullable bağlamını belirtir. Bu UI seçeneği Visual Studio 16,5 ' de tanıtılmıştı ve yalnızca C# 8,0 veya üstünü kullanan projeler için etkinleştirilmiştir.

Daha fazla bilgi için bkz. [Nullable bağlamları](/dotnet/csharp/nullable-references#nullable-contexts).

**32 bit tercih et**

**Prefer32 bit** onay kutusu işaretliyse, uygulama Windows 'un hem 32-bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışır. Onay kutusu silinirse, uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışır.

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

Hangi uyarıların hata olarak değerlendirilmediğini belirtmek için aşağıdaki ayarlar kullanılır. Derleme bir uyarıyla karşılaştığında bir hata döndürmek istediğiniz koşullar altında belirtmek için aşağıdaki seçeneklerden birini belirleyin. Daha fazla bilgi için bkz. [/warnaserror (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Hiçbiri** -hiçbir uyarı hata olarak kabul eder.

**Tümü** -tüm uyarıları hata olarak değerlendirir.

**Belirli uyarılar** -belirtilen uyarıları hata olarak değerlendirir. Birden çok uyarı numarasını virgül veya noktalı virgülle ayırın.

> [!TIP]
> Kod Analizi uyarılarının hata olarak değerlendirilmesini istemiyorsanız, bkz. [kod ANALIZI SSS](/visualstudio/code-quality/analyzers-faq#treat-warnings-as-errors).

## <a name="output"></a>Çıktı

Aşağıdaki ayarlar, yapı işlemi için çıkış seçeneklerini yapılandırmak üzere kullanılır.

**Çıkış yolu**

Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya girin veya bir yol belirtmek için, **tarayıcı** düğmesini seçin. Yol görelidir; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug veya bin\Release ' dir \\ .

Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md).

**XML belge dosyası**

Belge açıklamalarının işleneceği dosyanın adını belirtir. Daha fazla bilgi için [bkz. /doc (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**COM birlikte çalışma için kaydolma**

Yönetilen uygulamanıza com nesnesinin yönetilen uygulamayla etkileşim kurmasını sağlayan bir COM nesnesini (COM çağrılabilir sarmalayıcı) ortaya çıkartır. COM **birlikte** çalışma [](../../ide/reference/application-page-project-designer-visual-basic.md) özelliğine kaydolma özelliğinin kullanılabilir olması için, bu uygulama için **Proje** Tasarımcısı'nın Uygulama sayfasındaki Çıkış türü özelliğinin Sınıf Kitaplığı **olarak** ayarlanmış olması gerekir.  Uygulamanıza dahil olabileceğiniz ve BIR COM nesnesi olarak açığa çıkarabilirsiniz örnek [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] bir sınıf için [bkz. Örnek COM Sınıfı.](/dotnet/csharp/programming-guide/interop/example-com-class)

**Serileştirme derlemesi oluşturma**

Derleyicinin XML serileştirme derlemeleri oluşturmak için XML Serileştiricisi Oluşturma Aracı (Sgen.exe) kullanıp kullanmayacaklarını belirtir. Serileştirme derlemeleri, kodundaki türleri <xref:System.Xml.Serialization.XmlSerializer> serileştirmek için bu sınıfı kullandıysanız başlatma performansını geliştirebilir. Varsayılan olarak, bu seçenek Otomatik olarak ayarlanır ve bu, serileştirme derlemelerinin yalnızca kodundaki türleri XML'ye kodlamak için kullandıysanız <xref:System.Xml.Serialization.XmlSerializer> oluşturul olacağını belirtir. **Kapalı,** kodunuzun kullandığına bakılmaksızın seri hale getirme derlemelerinin asla oluşturulamay olmadığını <xref:System.Xml.Serialization.XmlSerializer> belirtir. **üzerinde,** serileştirme derlemelerinin her zaman oluşturul olacağını belirtir. Serileştirme derlemeleri, `TypeName`.XmlSerializers.dll. Daha fazla bilgi için [bkz. XML Serileştiricisi Oluşturma Aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Gelişmiş**

Gelişmiş Derleme Ayarları [İletişim Kutusu (C#) iletişim kutusunu görüntülemek](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) için tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
