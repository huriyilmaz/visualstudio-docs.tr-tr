---
title: Derleme sayfası, proje Tasarımcısı (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db830e04388b7465c941e2fdf069b49f98951a1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660834"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Derleme yönergelerini belirtmek için proje Tasarımcısı ' nın **derleme** sayfasını kullanın. Ayrıca, bu sayfada gelişmiş derleyici seçeneklerini ve derleme öncesi veya derleme sonrası olayları da belirtebilirsiniz.

 **Derle** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde, **Derle** sekmesine tıklayın.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve platform
 Aşağıdaki ayarlar, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. Bu nedenle, **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Yapılandırma** Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**veya **Tüm yapılandırmalardan**yapılır. Daha fazla bilgi için bkz. [hata ayıklama ve yayınlama projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) ve [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

 **Platform** Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. **Herhangi BIR CPU** (varsayılan), **x64**veya **x86**belirtebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="compiler-configuration-options"></a>Derleyici yapılandırma seçenekleri
 Aşağıdaki ayarlar, derleyici yapılandırma seçeneklerini ayarlamanıza olanak sağlar.

 **Derleme çıkış yolu** Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya yazın veya bir yol seçmek için, **Gözden** geçirme düğmesine tıklayın. Yolun göreli olduğunu unutmayın; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug\ veya bin\Release ' dir \\ . Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Seçenek açık** Değişkenlerin örtük bildirimine izin verilip verilmeyeceğini belirtir. Değişkenlerin açık bildirimini gerektirmek için **Açık '** ı seçin. Bu, değişkenlerin kullanılmadan önce bildirilmemiş olması durumunda derleyicinin hata raporlamasına neden olur. Örtük değişken bildirimine izin vermek için **kapalı** ' yı seçin.

 Bu ayar [/OptionExplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) derleyici seçeneğine karşılık gelir.

 Bir kaynak kodu dosyası [açık bir seçenek](https://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **Açık ayar seçeneğini** geçersiz kılar.

 Yeni bir proje oluşturduğunuzda, **derleme sayfasındaki** **Açık ayar seçeneği** , **Seçenekler** iletişim kutusundaki **Açık seçenek** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Açık seçenek** olan ilk varsayılan ayar **açıktır**.

 **Seçeneğinin açık** olarak ayarlanması `Off` , genellikle iyi bir uygulamadır. Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.

 **Option Strict** Katı tür semantiğinin zorlanıp zorlanmayacağını belirtir. **Option Strict** **Açık**olduğunda, aşağıdaki koşullar derleme zamanı hatasına neden olur:

- Örtük daraltma dönüşümleri

- Geç bağlama

- Bir tür ile sonuçlanan örtük yazma `Object`

  Örtük daraltma dönüştürme hataları, daraltma dönüştürmesi olan bir örtük veri türü dönüştürmesi olduğunda oluşur. Daha fazla bilgi için bkz. [Option Strict deyimin](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [örtük ve açık dönüştürmeler](https://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66), [genişletme ve daraltma dönüştürmeleri](https://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).

  Bir nesne, tür olarak belirtilen bir özelliğin veya yöntemin bir özelliğine atandığında geç bağlanır `Object` . Daha fazla bilgi için bkz. [Option Strict deyimin](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) yanı sıra [erken ve geç bağlama](https://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).

  Örtük nesne türü hataları, tanımlı bir değişken için uygun bir tür çıkarsanmadığında oluşur, bu nedenle bir türü `Object` algılanır. Bu öncelikle `Dim` , bir yan tümce kullanmadan bir değişkeni bildirmek için bir deyimi kullandığınızda oluşur `As` ve `Option Infer` kapalı olur. Daha fazla bilgi için bkz. [Option Strict deyimin](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer deyimleri](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)ve [Visual Basic Language belirtimi](https://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).

  **Katı ayarı seçeneği** , [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) derleyici seçeneğine karşılık gelir.

  Bir kaynak kodu dosyası bir [Option Strict ifadesini](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **katı** ayarını geçersiz kılar.

  Bir proje oluşturduğunuzda, **derleme sayfasındaki** **katı** ayarı **Seçenekler** iletişim kutusundaki **katı ayar seçeneğinin** değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Strict seçeneğinin** ilk varsayılan ayarı **kapalıdır**.

  **Kesin ayrı Uyarılar seçeneğini.** **Derleme sayfasının** **Uyarı yapılandırması** bölümü, açık olduğunda derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlara sahiptir `Option Strict` . Aşağıdaki ayarlar şunlardır:

- **Örtük dönüştürme**

- **Geç bağlama; çağrı çalışma zamanında başarısız olabilir**

- **Örtük tür; nesne varsayıldı**

  **Option Strict** **on on**olarak ayarlandığında, bu uyarı yapılandırma ayarlarının üçü de **hata**olarak ayarlanır. **Option Strict** ' i **off**olarak ayarlarsanız, üç ayar **hiçbiri None**olarak ayarlanır.

  Her uyarı yapılandırma ayarını **hiçbiri**, **Uyarı**veya **hata**olarak tek tek değiştirebilirsiniz. Üç uyarı yapılandırma ayarı **hata**olarak ayarlanırsa, `On` `Option strict` kutusunda görünür. Üçü de **hiçbiri**olarak ayarlandıysa, `Off` Bu kutuda görüntülenir. Bu ayarların diğer birleşimleri için **(özel)** görüntülenir.

  **Option Compare** Kullanılacak dize karşılaştırmasının türünü belirtir. Derleyicinin ikili, büyük/küçük harfe duyarlı dize karşılaştırmaları kullanmasını söylemek için **binary** ' ı seçin. Yerel ayara özgü, büyük/küçük harfe duyarsız metin dizesi karşılaştırmaları kullanmak için **metin** seçin.

  Bu ayar [/OptionCompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) derleyici seçeneğine karşılık gelir.

  Bir kaynak kodu dosyası bir [Seçenek karşılaştırma ekstresi](https://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e)içeriyorsa, `Binary` `Text` deyimdeki or değeri, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarını geçersiz kılar.

  Bir proje oluşturduğunuzda, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içindeki **Option Compare** 'In ilk varsayılan ayarı **binary**'dir.

  **Seçenek çıkarımı** Değişken bildirimlerinde yerel tür çıkarımını izin verilip verilmeyeceğini belirtir. Yerel tür çıkarımı kullanımına izin vermek için **Açık '** ı seçin. Yerel tür çıkarımı engellemek için **kapalı** ' yı seçin.

  Bu ayar [/OptionInfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) derleyici seçeneğine karşılık gelir.

  Bir kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **seçenek çıkarımı** ayarını geçersiz kılar.

  Bir proje oluşturduğunuzda, **derleme sayfasındaki** **seçenek çıkarımı** ayarı **Seçenekler** iletişim kutusundaki **seçenek çıkarımı** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak **seçenek çıkarımı** başlangıç varsayılan ayarı **Açık**olur.

  **Hedef CPU** Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** , her türlü 64 bit Intel uyumlu işlemci için **x64** , herhangi bir ARM işlemcisi için **ARM** veya herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** belirleyin. **Tüm CPU** , uygulamanın en çok sayıda donanım türünde çalışmasına izin verdiğinden yeni projeler için varsayılan değerdir.

  Daha fazla bilgi için bkz. [/Platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

  **32 bit tercih et** **Prefer32 bit** onay kutusu işaretliyse, uygulama Windows 'un hem 32-bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışır. Aksi takdirde, uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde 64 bit uygulama olarak çalışır.

  64 bitlik bir uygulama olarak çalıştırmak işaretçi boyutunu iki katına çıkarır ve yalnızca 32 bit olan kitaplıklarda uyumluluk sorunlarına neden olabilir. Bir uygulamayı yalnızca önemli ölçüde daha hızlı çalışıyorsa veya 4 GB 'den fazla belleğe ihtiyaç duyduğunda, 64 bit olarak çalıştırmak mantıklı olur.

  Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğru olduğunda kullanılabilir:

- **Derle sayfasında**, **hedef CPU** listesi **herhangi bir CPU**olarak ayarlanır.

- Uygulama **sayfasında**, **uygulama türü** listesi projenin bir uygulama olduğunu belirtir.

- **Uygulama sayfasında**, **hedef çerçeve** listesi 4,5 .NET Framework belirtir.

  **Uyarı konfigürasyonları** Bu tabloda, derleme koşulları ve ilgili bildirim düzeyi **yok**, **Uyarı**veya her biri için **hata** listelenmektedir.

  Varsayılan olarak, derleme sırasında tüm derleyici uyarıları Görev Listesi eklenir. Derleyicinin uyarı veya hata vermesine yol açmamasını sağlamak için **tüm uyarıları devre dışı bırak** ' ı seçin. Derleyicinin uyarıları düzeltilmesi gereken hata olarak görmesini istiyorsanız, **tüm uyarıları hata olarak değerlendir** ' i seçin.

  **Tüm uyarıları devre dışı bırak** Derleyicinin bu belgede daha önce açıklanan **koşul ve bildirim** tablosunda belirtilen bildirimleri vermesine izin verilip verilmeyeceğini belirtir. Varsayılan olarak bu onay kutusu işaretli değildir. Derleyicinin uyarı veya hata vermesine izin vermesini istemek için bu onay kutusunu seçin.

  Bu ayar, [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) derleyici seçeneğine karşılık gelir.

  **Tüm uyarıları hata olarak değerlendir** Uyarıların nasıl ele alınacağını belirtir. Varsayılan olarak, bu onay kutusu temizlenir, böylece tüm uyarı bildirimleri **Uyarı**olarak ayarlanır. Tüm uyarı bildirimlerini **hata**olarak değiştirmek için bu onay kutusunu işaretleyin.

  Bu seçenek yalnızca **tüm uyarıları devre dışı bırak** silinirse kullanılabilir.

  **XML belge dosyası oluştur** Belge bilgilerinin oluşturulup oluşturulmayacağını belirtir. Varsayılan olarak, bu onay kutusu seçilidir ve derleyici belge bilgilerini oluşturup bir XML dosyasına dahil eder. Derleyicinin belge oluşturmamasını istemek için bu onay kutusunu temizleyin.

  Bu ayar [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) derleyici seçeneğine karşılık gelir.

  **Com birlikte çalışması Için kaydolun** Yönetilen uygulamanızın, bir com nesnesinin uygulamayla etkileşime geçmesini sağlayan bir COM nesnesi (COM çağrılabilir sarmalayıcı) sergileip sunulmayacağını belirtir.

  Varsayılan olarak, bu onay kutusu temizlenir ve uygulamanın COM birlikte çalışabilirliğine izin vermemesi gerektiğini belirtir. COM birlikte çalışabilirliğine izin vermek için bu onay kutusunu seçin.

  Bu seçenek Windows uygulaması veya konsol uygulaması projeleri için kullanılamaz.

  **Derleme olayları** **Derleme olayları** iletişim kutusuna erişmek için bu düğmeye tıklayın. Proje için oluşturma öncesi ve derleme sonrası yapılandırma yönergelerini belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir. Daha fazla bilgi için bkz. [derleme olayları Iletişim kutusu (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

  **Gelişmiş derleme seçenekleri** **Advancedderleyici ayarları** iletişim kutusuna erişmek için bu düğmeye tıklayın. Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için **Advancedcompiler ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir. Daha fazla bilgi için bkz. [Gelişmiş derleyici ayarları Iletişim kutusu (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme özelliklerini yöneten](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) [proje yapılandırmalarının hatalarını ayıklama ve yayınlama](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) özellikleri [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Visual Basic komut satırı derleyicisi](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c) [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md)
