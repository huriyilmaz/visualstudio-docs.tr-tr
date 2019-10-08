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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9f121c4a95d719074e3004ee21e0d49d71e4c243
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000213"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)

Projenin derleme yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **Yapı** sayfasını kullanın. Bu sayfa yalnızca [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeleri için geçerlidir.

**Yapı** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Sonra menüdeki **Görünüm**, **Özellik sayfaları** ' nı seçin. Proje Tasarımcısı göründüğünde, **derleme** sekmesini seçin.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve platform

Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için [nasıl yapılır: Hata ayıklama ve yayın yapılandırmasını ayarlayın @ no__t-0.

**Yapılandırma**

Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarları **etkin (hata ayıklama)** (varsayılan), **hata ayıklama**, **yayın**veya **Tüm yapılandırmalardan**olabilir.

**Platformunun**

Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Varsayılan ayar **etkindir (herhangi BIR CPU)** . Etkin platformu **Configuration Manager**kullanarak değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Yapılandırma oluşturma ve düzenleme @ no__t-0.

## <a name="general"></a>Genel

Aşağıdaki seçenekler, çeşitli C# derleyici ayarlarını yapılandırmanızı sağlar.

**Koşullu derleme sembolleri**

Koşullu derlemenin gerçekleştirileceği sembolleri belirtir. Sembolleri noktalı virgül (";") ile ayırın. Daha fazla bilgi için bkz. [/defineC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**DEBUG sabitini tanımlayın**

Uygulamanızdaki tüm kaynak kodu dosyalarında bir sembol olarak hata ayıklamayı tanımlar. Bunu seçmek, `/define:DEBUG` komut satırı seçeneğini kullanmaya eşdeğerdir.

**TRACE sabitini tanımlayın**

Uygulamanızı uygulamanızdaki tüm kaynak kodu dosyalarında sembol olarak tanımlar. Bunu seçmek, `/define:TRACE` komut satırı seçeneğini kullanmaya eşdeğerdir.

**Platform hedefi**

Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** seçeneğini belirleyin, her 64 bit Intel uyumlu işlemci için **x64** seçeneğini belirleyin, ARM işlemcileri için **ARM** 'yi seçin ya da herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** seçin. **Tüm CPU** , uygulamanın en geniş donanım yelpazesi üzerinde çalışmasına izin verdiğinden projeler için varsayılan değerdir.

Daha fazla bilgi için bkz. [/PlatformC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**32 bit tercih et**

**Prefer32 bit** onay kutusu işaretliyse, uygulama Windows 'un hem 32-bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışır. Onay kutusu silinirse, uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışır.

Bir uygulamayı 64 bitlik bir uygulama olarak çalıştırırsanız, işaretçi boyutu iki katına çıkar ve uyumluluk sorunları, özel olarak 32 bit olan diğer kitaplıklarla meydana gelebilir. 64 bitlik bir uygulamayı yalnızca 4 GB 'den fazla bellek gerekiyorsa veya 64 bit yönergeler önemli bir performans geliştirmesi sağlamak için yararlıdır.

Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğru olduğunda kullanılabilir:

- **Yapı sayfasında**, **Platform hedefi** listesi **herhangi bir CPU**olarak ayarlanır.

- **Uygulama sayfasında**, **Çıkış türü** listesi projenin bir uygulama olduğunu belirtir.

- **Uygulama sayfasında**, **hedef çerçeve** listesi 4,5 .NET Framework belirtir.

**Güvenli olmayan koda izin ver**

Derlemek için [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) anahtar sözcüğünü kullanan koda izin verir. Daha fazla bilgi için bkz. [/unsafeC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Kodu En İyileştir**

Çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen iyileştirmeleri etkinleştirin veya devre dışı bırakın. Daha fazla bilgi için bkz. [/optimizeC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar

Aşağıdaki ayarlar, yapı işlemi için hata ve uyarı seçeneklerini yapılandırmak için kullanılır.

**Uyarı düzeyi**

Derleyici uyarılarının görüntüleneceği düzeyi belirtir. Daha fazla bilgi için bkz. [/WarnC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Uyarıları bastır**

Derleyicinin bir veya daha fazla uyarı oluşturma yeteneğini engeller. Birden çok uyarı numarasını virgül veya noktalı virgülle ayırın. Daha fazla bilgi için bkz. [/nowarnC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir

Hangi uyarıların hata olarak değerlendirilmediğini belirtmek için aşağıdaki ayarlar kullanılır. Derleme bir uyarıyla karşılaştığında bir hata döndürmek istediğiniz koşullar altında belirtmek için aşağıdaki seçeneklerden birini belirleyin. Daha fazla bilgi için bkz. [/warnaserrorC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Hiçbiri** -hiçbir uyarı hata olarak kabul eder.

**Tümü** -tüm uyarıları hata olarak değerlendirir.

**Belirli uyarılar** -belirtilen uyarıları hata olarak değerlendirir. Birden çok uyarı numarasını virgül veya noktalı virgülle ayırın.

> [!TIP]
> Kod Analizi uyarılarının hata olarak değerlendirilmesini istemiyorsanız, bkz. [kod ANALIZI SSS](../../code-quality/analyzers-faq.md#treat-warnings-as-errors).

## <a name="output"></a>Output

Aşağıdaki ayarlar, yapı işlemi için çıkış seçeneklerini yapılandırmak üzere kullanılır.

**Çıkış yolu**

Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya girin veya bir yol belirtmek için, **tarayıcı** düğmesini seçin. Yol görelidir; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug veya bin\Release @ no__t-0 ' dır.

Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md).

**XML belge dosyası**

Belge açıklamalarının işleneceği dosyanın adını belirtir. Daha fazla bilgi için bkz. [/docC# (derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**COM birlikte çalışması için kaydolun**

Yönetilen uygulamanızın bir com nesnesi (com çağrılabilir sarmalayıcı) sergilediğini, bu sayede bir COM nesnesinin yönetilen uygulamanızla etkileşime geçmesini sağlar. Bu uygulama için **Proje Tasarımcısı** 'nın [Uygulama sayfasındaki](../../ide/reference/application-page-project-designer-visual-basic.md) **Çıkış türü** özelliği, **com birlikte çalışma** özelliğinin kullanılabilir olmasını sağlamak için **sınıf kitaplığı** olarak ayarlanmalıdır. @No__t-0 uygulamanıza dahil olabileceğiniz ve bir COM nesnesi olarak kullanıma sunabileceğiniz örnek bir sınıf için bkz. [örnek com sınıfı](/dotnet/csharp/programming-guide/interop/example-com-class).

**Serileştirme bütünleştirilmiş kodu oluştur**

Derleyicinin XML serileştirme derlemeleri oluşturmak için XML Serileştiricisi Oluşturma Aracı (SGen. exe) kullanıp kullanmayacağını belirtir. Kodunuzda türleri seri hale getirmek için bu sınıfı kullandıysanız, serileştirme derlemeleri <xref:System.Xml.Serialization.XmlSerializer> ' ın başlangıç performansını iyileştirebilir. Varsayılan olarak, bu seçenek **Auto**olarak ayarlanır, bu da serileştirme derlemelerinin yalnızca KODUNUZDA türleri XML olarak kodlamak için <xref:System.Xml.Serialization.XmlSerializer> kullandıysanız oluşturulmasını belirtir. **Kapalı** , kodunuzun <xref:System.Xml.Serialization.XmlSerializer> ' i kullanıp kullanmadığına bakılmaksızın serileştirme derlemelerinin hiçbir şekilde üretilmediğini belirtir. **On** , serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme bütünleştirilmiş kodları `TypeName` olarak adlandırılır. Xmlserileştiriciler. dll. Daha fazla bilgi için bkz. [XML serileştiricisi oluşturma aracı (SGen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Gelişmiş**

[Gelişmiş derleme ayarları iletişim kutusu (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) iletişim kutusunu göstermek için tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)