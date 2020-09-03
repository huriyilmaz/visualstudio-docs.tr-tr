---
title: Derleme sayfası, proje Tasarımcısı (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21b572e99d23c882f90a1e9218e7a52fb94aedb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660903"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenin derleme yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **Yapı** sayfasını kullanın. Bu sayfa [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yalnızca projeler için geçerlidir.

 **Yapı** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde, **derleme** sekmesine tıklayın.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve platform
 Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Yapılandırma** Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarları **etkin (hata ayıklama)** (varsayılan), **hata ayıklama**, **yayın**veya **Tüm yapılandırmalardan**olabilir.

 **Platform** Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Varsayılan ayar **etkindir (herhangi BIR CPU)**. Etkin platformu **Configuration Manager**kullanarak değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Genel
 Aşağıdaki seçenekler, çeşitli C# derleyici ayarlarını yapılandırmanızı sağlar.

 **Koşullu derleme sembolleri** Koşullu derlemenin gerçekleştirileceği sembolleri belirtir. Sembolleri noktalı virgül (";") ile ayırın. Daha fazla bilgi için bkz. [/define (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).

 **Hata ayıklama sabiti tanımla** Uygulamanızdaki tüm kaynak kodu dosyalarında bir sembol olarak hata ayıklamayı tanımlar. Bunu seçtiğinizde, `/define:DEBUG` komut satırı seçeneği kullanılarak eşdeğerdir.

 **İzleme sabitini tanımlama** Uygulamanızı uygulamanızdaki tüm kaynak kodu dosyalarında sembol olarak tanımlar. Bunu seçtiğinizde, `/define:TRACE` komut satırı seçeneği kullanılarak eşdeğerdir.

 **Hedef CPU** Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** seçeneğini belirleyin, her 64 bit Intel uyumlu işlemci için **x64** seçeneğini belirleyin, ARM işlemcileri için **ARM** 'yi seçin ya da herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** seçin. **Tüm CPU** , uygulamanın en geniş donanım yelpazesi üzerinde çalışmasına izin verdiğinden projeler için varsayılan değerdir.

 Daha fazla bilgi için bkz. [/Platform (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).

 **32 bit tercih et** **Prefer32 bit** onay kutusu işaretliyse, uygulama Windows 'un hem 32-bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışır. Onay kutusu silinirse, uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışır.

 Bir uygulamayı 64 bitlik bir uygulama olarak çalıştırırsanız, işaretçi boyutu iki katına çıkar ve uyumluluk sorunları, özel olarak 32 bit olan diğer kitaplıklarla meydana gelebilir. 64 bitlik bir uygulamayı yalnızca 4 GB 'den fazla bellek gerekiyorsa veya 64 bit yönergeler önemli bir performans geliştirmesi sağlamak için yararlıdır.

 Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğru olduğunda kullanılabilir:

- **Yapı sayfasında**, **Platform hedefi** listesi **herhangi bir CPU**olarak ayarlanır.

- **Uygulama sayfasında**, **Çıkış türü** listesi projenin bir uygulama olduğunu belirtir.

- **Uygulama sayfasında**, **hedef çerçeve** listesi 4,5 .NET Framework belirtir.

  **Güvenli olmayan koda Izin ver** Derlemek için [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) anahtar sözcüğünü kullanan koda izin verir. Daha fazla bilgi için bkz. [/unsafe (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).

  **Kodu iyileştirme** Çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen iyileştirmeleri etkinleştirin veya devre dışı bırakın. Daha fazla bilgi için bkz. [/optimize (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar
 Aşağıdaki ayarlar, yapı işlemi için hata ve uyarı seçeneklerini yapılandırmak için kullanılır.

 **Uyarı düzeyi** Derleyici uyarılarının görüntüleneceği düzeyi belirtir. Daha fazla bilgi için bkz. [/Warn (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).

 **Uyarıları bastır** Derleyicinin bir veya daha fazla uyarı oluşturma yeteneğini engeller. Birden çok uyarı numarasını virgül veya noktalı virgülle ayırın. Daha fazla bilgi için bkz. [/nowarn (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir
 Hangi uyarıların hata olarak değerlendirilmediğini belirtmek için aşağıdaki ayarlar kullanılır. Derleme bir uyarıyla karşılaştığında bir hata döndürmek istediğiniz koşullar altında belirtmek için aşağıdaki seçeneklerden birini belirleyin. Daha fazla bilgi için bkz. [/warnaserror (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).

 **Hiçbiri** Hata olarak uyarı vermez.

 **Belirli uyarılar** Belirtilen uyarıları hata olarak değerlendirir. Birden çok uyarı numarasını virgül veya noktalı virgülle ayırın.

 **Tümü** Tüm uyarıları hata olarak değerlendirir.

## <a name="output"></a>Çıktı
 Aşağıdaki ayarlar, yapı işlemi için çıkış seçeneklerini yapılandırmak üzere kullanılır.

 **Çıkış yolu** Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya girin veya bir yol belirtmek için, **tarayıcı** düğmesini seçin. Yolun göreli olduğunu unutmayın; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug veya bin\Release ' dir \\ . Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **XML belge dosyası** Belge açıklamalarının işleneceği dosyanın adını belirtir. Daha fazla bilgi için bkz. [/doc (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).

 **Com birlikte çalışması Için kaydolun** Yönetilen uygulamanızın bir com nesnesi (com çağrılabilir sarmalayıcı) sergilediğini, bu sayede bir COM nesnesinin yönetilen uygulamanızla etkileşime geçmesini sağlar. Bu uygulama için **Proje Tasarımcısı** 'nın [Uygulama sayfasındaki](../../ide/reference/application-page-project-designer-visual-basic.md) **Çıkış türü** özelliği, **com birlikte çalışma** özelliğinin kullanılabilir olmasını sağlamak için **sınıf kitaplığı** olarak ayarlanmalıdır. Uygulamanıza dahil olabileceğiniz [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve bır com nesnesi olarak kullanıma sunabileceğiniz örnek bir sınıf için bkz. [örnek com sınıfı](https://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).

 **Serileştirme bütünleştirilmiş kodu oluştur** Derleyicinin XML serileştirme derlemeleri oluşturmak için XML Serileştiricisi Oluşturma Aracı (Sgen.exe) kullanıp kullanmayacağını belirtir. <xref:System.Xml.Serialization.XmlSerializer>Kodunuzda türleri seri hale getirmek için bu sınıfı kullandıysanız, serileştirme derlemeleri ' nin başlangıç performansını iyileştirebilir. Varsayılan olarak, bu seçenek **Auto**olarak ayarlanır, bu da serileştirme derlemelerinin yalnızca <xref:System.Xml.Serialization.XmlSerializer> kodunuzda türleri XML olarak kodlamak için kullandıysanız oluşturulacağını belirtir. **Kapalı** , kodunuzun kullanıp kullanmadığına bakılmaksızın serileştirme derlemelerinin hiçbir şekilde üretilmediğini belirtir <xref:System.Xml.Serialization.XmlSerializer> . **On** , serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme bütünleştirilmiş kodları.XmlSerializers.dll olarak adlandırılır `TypeName` . Daha fazla bilgi için bkz. [XML serileştiricisi oluşturma aracı (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).

 **Gelişmiş** [Gelişmiş derleme ayarları Iletişim kutusu (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) iletişim kutusunu göstermek için tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Proje Özellikleri başvurusu](../../ide/reference/project-properties-reference.md) [C# derleyici seçenekleri](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
