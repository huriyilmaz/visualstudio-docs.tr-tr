---
title: Derleme Sayfası, Proje Tasarımcısı (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7a97068b70a76dfe343de5fa68db77d2ce9781
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111314"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)

Derleme yönergelerini belirtmek için Proje Tasarımcısının **Derleme** sayfasını kullanın. Ayrıca, bu sayfada gelişmiş derleyici seçenekleri ve önceden oluşturma veya oluşturma sonrası olayları da belirtebilirsiniz.

**Derle** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin. Ardından menü çubuğundaki **Project**, **Özellikler'i** seçin. Proje Tasarımcısı göründüğünde, **Derle** sekmesini tıklatın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki ayarlar, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak tanır.

> [!NOTE]
> Basitleştirilmiş yapı yapılandırmalarıyla, proje sistemi hata ayıklama mı yoksa sürüm sürümü mü oluşturup oluşturmayacağını belirler. Bu nedenle, **Yapılandırma** ve **Platform** listeleri görüntülenmez.

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntülenecin veya değiştirilen leri belirtir. Ayarlar **Hata Ayıklama** (varsayılan), **Sürüm**veya **Tüm Yapılandırmaları**vardır. Daha fazla bilgi için bkz: [Yapı Yapılandırmalarını Anlama](../../ide/understanding-build-configurations.md) ve [Nasıl Yapılacağını: Yapılandırmaları Oluştur ve Düzenleme.](../../ide/how-to-create-and-edit-configurations.md)

**Platform**

Hangi platform ayarlarının görüntüleneceğin veya değiştirilen leri belirtir. **Herhangi bir CPU** (varsayılan), **x64**veya **x86**belirtebilirsiniz.

## <a name="compiler-configuration-options"></a>Derleyici Yapılandırma Seçenekleri

Aşağıdaki ayarlar derleyici yapılandırma seçeneklerini ayarlamanızı sağlar.

**Çıkış yolu oluşturma**

Bu projenin yapılandırması için çıktı dosyalarının konumunu belirtir. Bu kutuya yapı çıktısının yolunu yazın veya bir yol seçmek için **Gözat** düğmesini tıklatın. Yolun göreceli olduğunu unutmayın; mutlak bir yol girerseniz, göreceli olarak kaydedilir. Varsayılan yol bin\Debug\ veya bin\Release'\\dir.

Basitleştirilmiş yapı yapılandırmalarıyla, proje sistemi hata ayıklama mı yoksa sürüm sürümü mü oluşturup oluşturmayacağını belirler. **Hata Ayıklama** menüsünden (F5) **Yapı** komutu, belirttiğiniz **Çıktı yolundan** bağımsız olarak yapıyı hata ayıklama konumuna koyar. Ancak, **Yapı** menüsünden **Yap** komutu, onu belirttiğiniz konuma koyar.

**Seçenek açık**

Değişkenlerin örtülü bildirimine izin verilip verilip vermeyeceğini belirtir. Değişkenlerin açık bildirimini istemek için **Açık'ı** seçin. Bu, değişkenler kullanılmadan önce bildirilmemişse derleyicinin hataları bildirmesine neden olur. Değişkenlerin örtülü bildirimine izin vermek için **Kapalı'yı** seçin.

Bu ayar [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) derleyici seçeneğine karşılık gelir.

Kaynak kod dosyasında [Bir Seçenek Açık İfadesi](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)varsa, `On` deyimdeki `Off` veya değer **Derle sayfasındaki** **Açık Seçenek** ayarını geçersiz kılar.

Yeni bir proje oluşturduğunuzda, Derleme **sayfasındaki** **Açık Seçenek** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek Açık** ayarına ayarlanır. **Araçlar** menüsündeki bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için **Seçenekler'i**tıklatın. **Seçenekler** iletişim **kutusunda, Projeler ve Çözümler'i**genişletin ve ardından **VB Varsayılanları'nı**tıklatın. **VB Varsayılanlarında** **Açık Seçeneğin** ilk varsayılan ayarı **Açık'tır.**

**Seçenek Açık'ı** `Off` ayarlamak genellikle iyi bir uygulama değildir. Bir veya daha fazla konumda bir değişken adını yanlış yazabilirsiniz, bu da program çalıştırıldığında beklenmeyen sonuçlara neden olabilir.

**Seçenek sıkı**

Katı tip semantik lerinin uygulanıp uygulanmayacağını belirtir. **Seçenek Katı** **A'da**olduğunda, aşağıdaki koşullar derleme zamanı hatasına neden olur:

- Örtülü daraltma dönüşümleri

- Geç bağlama

- Bir `Object` türle sonuçlanan örtük yazma

Örtülü daraltma dönüştürme hataları, daralan bir dönüştürme olan örtülü bir veri türü dönüştürme olduğunda oluşur. Daha fazla bilgi için, [Seçenek Katı Bildirimi,](/dotnet/visual-basic/language-reference/statements/option-strict-statement) [Örtük ve Açık Dönüşümler](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)ve [Dönüşümleri Genişletme ve Daraltma'ya](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)bakın.

Bir nesne, tür `Object`de olduğu bildirilen bir değişkenin bir özelliğine veya yöntemine atandığında geç bağlanır. Daha fazla bilgi için, [Seçenek Sıkı Bildirimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement) ve Erken ve Geç [Bağlama'ya](/dotnet/visual-basic/programming-guide/language-features/early-late-binding)bakın.

Beyan edilen bir değişken için uygun bir tür çıkarılamıyorsa, örtük nesne türü hataları oluşur, bu nedenle bir tür `Object` çıkarılır. Bu, öncelikle bir `Dim` `As` yan tümce kullanmadan bir değişkeni `Option Infer` bildirmek için bir deyim kullandığınızda ve kapalıyken oluşur. Daha fazla bilgi için, [Bkz. Seçenek Katı Bildirimi,](/dotnet/visual-basic/language-reference/statements/option-strict-statement) [Seçenek Infer Bildirimi](/dotnet/visual-basic/language-reference/statements/option-infer-statement)ve [Görsel Temel Dil Belirtimi.](/dotnet/visual-basic/reference/language-specification)

**Seçenek Katı** ayarı [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) derleyici seçeneğine karşılık gelir.

Kaynak kod dosyası nda Bir Seçenek `On` Katı `Off` [Bildirimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement)varsa, deyimdeki veya değer **Derle sayfasındaki** **Seçenek Katı** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **Derleme sayfasındaki** **Sıkı Seçenek** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek Katı** ayarı değerine ayarlanır. **Araçlar** menüsündeki bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için **Seçenekler'i**tıklatın. **Seçenekler** iletişim **kutusunda, Projeler ve Çözümler'i**genişletin ve ardından **VB Varsayılanları'nı**tıklatın. **VB Defaults'ta** **Katı Seçenek'in** ilk varsayılan ayarı **Kapalıdır.**

**Seçenek Sıkı Bireysel Uyarılar**

**Derle** sayfasının Uyarı `Option Strict` **yapılandırmaları** bölümünde, üzerinde yken derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlar vardır. Aşağıdaki ayarları şunlardır:

- **Örtük dönüştürme**

- **Geç ciltleme; arama çalışma zamanında başarısız olabilir**

- **Örtük tür; nesne kabul**

**Seçenek Katı'yı** **A'ya**ayarladığınızda, bu uyarı yapılandırma ayarlarının üçü de **Hata**olarak ayarlanır. **Seçenek Katı'yı** **Kapalı**olarak ayarladığınızda, üç ayar da **Yok**olarak ayarlanır.

Her uyarı yapılandırma ayarını Tek tek **None,** **Warning**veya **Error**olarak değiştirebilirsiniz. Her üç uyarı yapılandırma ayarları **Error**hata `On` olarak ayarlanırsa, `Option strict` kutusunda görünür. Üçü de **Yok**olarak `Off` ayarlanmışsa, bu kutuda görünür. Bu ayarların başka bir birleşimi **için (özel)** görüntülenir.

**Seçenek karşılaştırma**

Kullanılacak dize karşılaştırması türünü belirtir. Derleyiciye ikili, büyük/küçük harf duyarlı dize karşılaştırmalarını kullanmasını öğretmek için **İkili'yi** seçin. Yerele özgü, büyük/küçük harf duyarlı metin dize karşılaştırmalarını kullanmak için **Metin'i** seçin.

Bu ayar [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) derleyici seçeneğine karşılık gelir.

Kaynak kod dosyası nda [Opsiyon Karşılaştırma](/dotnet/visual-basic/language-reference/statements/option-compare-statement) `Binary` Bildirimi `Text` varsa, deyimdeki veya değer **Derle sayfasındaki** **Seçenek Karşılaştırma** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **Derle sayfasındaki** **Seçenek Karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek Karşılaştırma** ayarının değerine ayarlanır. **Araçlar** menüsündeki bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için **Seçenekler'i**tıklatın. **Seçenekler** iletişim **kutusunda, Projeler ve Çözümler'i**genişletin ve ardından **VB Varsayılanları'nı**tıklatın. **VB Defaults'ta** **Opsiyon Karşılaştırması'nın** ilk varsayılan ayarı **İkili'dir.**

**Seçenek çıkartı**

Değişken bildirimlerde yerel tür çıkarımlarına izin verilip verilmeyeceğini belirtir. Yerel tür çıkarımını kullanmak için **On'u** seçin. Yerel tür çıkarımlarını engellemek için **Kapalı'yı** seçin.

Bu ayar [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) derleyici seçeneğine karşılık gelir.

Kaynak kod dosyası nda [Bir Seçenek ÇıkarTisi Bildirimi](/dotnet/visual-basic/language-reference/statements/option-infer-statement)varsa, deyimdeki `On` veya `Off` değer **Derle sayfasındaki** **Seçenek Çıkarı** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **Derle sayfasındaki** **Seçenek Çıkarı** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek Çıkartı** ayarı değerine ayarlanır. **Araçlar** menüsündeki bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için **Seçenekler'i**tıklatın. **Seçenekler** iletişim **kutusunda, Projeler ve Çözümler'i**genişletin ve ardından **VB Varsayılanları'nı**tıklatın. **VB Varsayılanlar'da** **Opsiyon Çıkarı'nın** ilk varsayılan ayarı **Açıktır.**

**Hedef CPU**

İşlemcinin çıktı dosyası tarafından hedef alınmasını belirtir. Herhangi bir 32-bit Intel uyumlu işlemci için **x86** belirtin, herhangi bir 64-bit Intel uyumlu işlemci için **x64,** herhangi bir ARM işlemci için **ARM,** veya herhangi bir işlemci kabul edilebilir olduğunu belirtmek için **herhangi bir CPU.** **Herhangi bir CPU,** uygulamanın en çok sayıda donanım türünde çalışmasına izin verdiği için yeni projeler için varsayılan değerdir.

Daha fazla bilgi için bkz: [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**32 bit tercih etmeyi tercih edin**

**Prefer32-bit** onay kutusu seçilirse, uygulama Windows'un hem 32 bit hem de 64 bit sürümlerinde 32 bit uygulama olarak çalışır. Aksi takdirde, uygulama Windows'un 32 bit sürümlerinde 32 bit uygulama ve Windows'un 64 bit sürümlerinde 64 bit uygulama olarak çalışır.

64 bit uygulama olarak çalışan işaretçi boyutunu iki katına çıkarır ve yalnızca 32 bit olan kitaplıklarla uyumluluk sorunlarına neden olabilir. Bir uygulamayı yalnızca önemli ölçüde daha hızlı çalışıyorsa veya 4 GB'dan fazla belleğe ihtiyaç duyduğunda 64 bit olarak çalıştırmak mantıklıdır.

Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa kullanılabilir:

- **Derle Sayfasında,** **Hedef CPU** listesi Herhangi **bir CPU**olarak ayarlanır.

- Uygulama **Sayfasında,** **Uygulama türü** listesi projenin bir uygulama olduğunu belirtir.

- Uygulama **Sayfasında**, **Hedef çerçeve** listesi .NET Framework 4.5'i belirtir.

**Uyarı yapılandırmaları**

Bu tablo, yapı koşullarını ve her biri için **Yok**, **Uyarı**veya **Hata'nın** karşılık gelen bildirim düzeyini listeler.

Varsayılan olarak, derleme sırasında tüm derleyici uyarıları Görev Listesi'ne eklenir. Derleyiciye uyarı veya hata vermemetalimatı vermek için **tüm uyarıları devre dışı** tanıt'ı seçin. Derleyicinin uyarıları düzeltilmesi gereken hatalar olarak ele almasını istiyorsanız **tüm uyarıları hata olarak değerlendir'i** seçin.

**Tüm uyarıları devre dışı**

Derleyicinin bu belgede daha önce açıklanan **Koşul ve Bildirim** tablosunda belirtildiği gibi bildirim ler yayınlamasına izin verilip verilmeyeceğini belirtir. Varsayılan olarak bu onay kutusu işaretli değildir. Derleyiciye uyarı veya hata vermemelerini söylemek için bu onay kutusunu seçin.

Bu ayar [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) derleyici seçeneğine karşılık gelir.

**Tüm uyarıları hata olarak değerlendirin**

Uyarıların nasıl tedavi edilebildiğini belirtir. Varsayılan olarak, bu onay kutusu temizlenir, böylece tüm uyarı bildirimleri **Uyarı**olarak ayarlanır. Tüm uyarı bildirimlerini **Hata**olarak değiştirmek için bu onay kutusunu seçin.

Bu seçenek yalnızca **tüm uyarıları devre dışı kılırsa** kullanılabilir.

**XML dokümantasyon dosyası oluşturma**

Belge bilgilerinin oluşturup oluşturmayacağını belirtir. Varsayılan olarak, bu onay kutusu seçilir ve derleyiciye belge bilgilerini oluşturmasını ve bir XML dosyasına eklemesini bildirir. Derleyiciye belge oluşturmamasını söylemek için bu onay kutusunu temizleyin.

Bu ayar [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) derleyici seçeneğine karşılık gelir.

**COM interop'a kaydolun**

Yönetilen uygulamanızın, com nesnesinin uygulamayla etkileşimkurmasını sağlayan bir COM nesnesini (COM çağrılabilir sarıcı) ortaya çıkaracağını belirtir.

Varsayılan olarak, bu onay kutusu temizlenir ve uygulamanın COM interop'a izin vermeyeceği belirtilir. COM interop'a izin vermek için bu onay kutusunu seçin.

Bu seçenek Windows Application veya Console Application projeleri için kullanılamaz.

**Etkinlikler Oluşturun**

**Etkinlikler Oluştur** iletişim kutusuna erişmek için bu düğmeyi tıklatın. Proje için önceden yapı ve yapı sonrası yapılandırma yönergelerini belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için, [Etkinlikler Oluştur İletişim Kutusu 'na (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md)bakın.

**Gelişmiş Derleme Seçenekleri**

**AdvancedCompiler Ayarları** iletişim kutusuna erişmek için bu düğmeyi tıklatın. Projenin gelişmiş yapı yapılandırma özelliklerini belirtmek için **AdvancedCompiler Ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için [Gelişmiş Derleyici Ayarları İletişim Kutusu 'na (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic Command-Line Derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)
