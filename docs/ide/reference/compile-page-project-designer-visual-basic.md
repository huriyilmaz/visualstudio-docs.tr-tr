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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfe552db89da4cb4d2a9782a1b5d2c8468833baa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654579"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)

Derleme yönergelerini belirtmek için proje Tasarımcısı ' nın **derleme** sayfasını kullanın. Ayrıca, bu sayfada gelişmiş derleyici seçeneklerini ve derleme öncesi veya derleme sonrası olayları da belirtebilirsiniz.

**Derle** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. Ardından, menü çubuğunda **Proje**, **Özellikler** ' i seçin. Proje Tasarımcısı göründüğünde, **Derle** sekmesine tıklayın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve platform

Aşağıdaki ayarlar, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. Bu nedenle, **yapılandırma** ve **Platform** listeleri görüntülenmez.

**Yapılandırma**

Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**veya **Tüm yapılandırmalardan**yapılır. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md) ve [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

**Platformunun**

Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. **Herhangi BIR CPU** (varsayılan), **x64**veya **x86**belirtebilirsiniz.

## <a name="compiler-configuration-options"></a>Derleyici yapılandırma seçenekleri

Aşağıdaki ayarlar, derleyici yapılandırma seçeneklerini ayarlamanıza olanak sağlar.

**Derleme çıkış yolu**

Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya yazın veya bir yol seçmek için, **Gözden** geçirme düğmesine tıklayın. Yolun göreli olduğunu unutmayın; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug\ veya bin\Release \\.

Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar.

**Seçenek açık**

Değişkenlerin örtük bildirimine izin verilip verilmeyeceğini belirtir. Değişkenlerin açık bildirimini gerektirmek için **Açık '** ı seçin. Bu, değişkenlerin kullanılmadan önce bildirilmemiş olması durumunda derleyicinin hata raporlamasına neden olur. Örtük değişken bildirimine izin vermek için **kapalı** ' yı seçin.

Bu ayar [/OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [seçenek açık ifade](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)içeriyorsa, deyimdeki `On` veya `Off` değeri, **derleme sayfasındaki**açık ayar **seçeneğini** geçersiz kılar.

Yeni bir proje oluşturduğunuzda, **derleme sayfasındaki** **Açık ayar seçeneği** , **Seçenekler** iletişim kutusundaki **Açık seçenek** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Açık seçenek** olan ilk varsayılan ayar **açıktır**.

@No__t_1 **seçeneğinin açık** ayarı genellikle iyi bir uygulamadır. Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.

**Option Strict**

Katı tür semantiğinin zorlanıp zorlanmayacağını belirtir. **Option Strict** **Açık**olduğunda, aşağıdaki koşullar derleme zamanı hatasına neden olur:

- Örtük daraltma dönüşümleri

- Geç bağlama

- @No__t_0 türü ile sonuçlanan örtük yazma

Örtük daraltma dönüştürme hataları, daraltma dönüştürmesi olan bir örtük veri türü dönüştürmesi olduğunda oluşur. Daha fazla bilgi için bkz. [Option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [örtük ve açık dönüştürmeler](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), [genişletme ve daraltma dönüştürmeleri](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Bir nesne, `Object` türünde olduğu bildirilmiştir bir özelliğin ya da yönteminin bir özelliğine atandığında geç bağlanır. Daha fazla bilgi için bkz. [Option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement) yanı sıra [erken ve geç bağlama](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Örtük nesne türü hataları, tanımlı bir değişken için uygun bir tür çıkarsanmadığında oluşur, bu nedenle bir `Object` türü algılanır. Bu öncelikle bir `As` yan tümcesi kullanmadan bir değişkeni bildirmek için bir `Dim` deyimi kullandığınızda oluşur ve `Option Infer` kapalı olur. Daha fazla bilgi için bkz. [Option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer deyimleri](/dotnet/visual-basic/language-reference/statements/option-infer-statement)ve [Visual Basic Language belirtimi](/dotnet/visual-basic/reference/language-specification).

**Katı ayarı seçeneği** , [/OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [Option Strict ifadesini](/dotnet/visual-basic/language-reference/statements/option-strict-statement)içeriyorsa, deyimdeki `On` veya `Off` değeri, **derleme sayfasındaki** **katı** ayarı geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **katı** ayarı **Seçenekler** iletişim kutusundaki **katı ayar seçeneğinin** değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Strict seçeneğinin** ilk varsayılan ayarı **kapalıdır**.

**İsteğe bağımsız kesin uyarılar**

**Derleme sayfasının** **Uyarı yapılandırması** bölümü, `Option Strict` olduğunda derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlara sahiptir. Aşağıdaki ayarlar şunlardır:

- **Örtük dönüştürme**

- **Geç bağlama; çağrı çalışma zamanında başarısız olabilir**

- **Örtük tür; nesne varsayıldı**

**Option Strict** **on on**olarak ayarlandığında, bu uyarı yapılandırma ayarlarının üçü de **hata**olarak ayarlanır. **Option Strict** ' i **off**olarak ayarlarsanız, üç ayar **hiçbiri None**olarak ayarlanır.

Her uyarı yapılandırma ayarını **hiçbiri**, **Uyarı**veya **hata**olarak tek tek değiştirebilirsiniz. Üç uyarı yapılandırma ayarı **hata**olarak ayarlanırsa, `On` `Option strict` kutusunda görünür. Üçü de **hiçbiri**olarak ayarlandıysa, bu kutuda `Off` görüntülenir. Bu ayarların diğer birleşimleri için **(özel)** görüntülenir.

**Option Compare**

Kullanılacak dize karşılaştırmasının türünü belirtir. Derleyicinin ikili, büyük/küçük harfe duyarlı dize karşılaştırmaları kullanmasını söylemek için **binary** ' ı seçin. Yerel ayara özgü, büyük/küçük harfe duyarsız metin dizesi karşılaştırmaları kullanmak için **metin** seçin.

Bu ayar [/OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [Seçenek karşılaştırma ekstresi](/dotnet/visual-basic/language-reference/statements/option-compare-statement)içeriyorsa, deyimdeki `Binary` veya `Text` değeri, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içindeki **Option Compare** 'In ilk varsayılan ayarı **binary**'dir.

**Seçenek çıkarımı**

Değişken bildirimlerinde yerel tür çıkarımını izin verilip verilmeyeceğini belirtir. Yerel tür çıkarımı kullanımına izin vermek için **Açık '** ı seçin. Yerel tür çıkarımı engellemek için **kapalı** ' yı seçin.

Bu ayar [/OptionInfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](/dotnet/visual-basic/language-reference/statements/option-infer-statement)içeriyorsa, deyimdeki `On` veya `Off` değeri, **derleme sayfasındaki** **seçenek çıkarımı** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **seçenek çıkarımı** ayarı **Seçenekler** iletişim kutusundaki **seçenek çıkarımı** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak **seçenek çıkarımı** başlangıç varsayılan ayarı **Açık**olur.

**Hedef CPU**

Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** , her türlü 64 bit Intel uyumlu işlemci için **x64** , herhangi bir ARM işlemcisi için **ARM** veya herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** belirleyin. **Tüm CPU** , uygulamanın en çok sayıda donanım türünde çalışmasına izin verdiğinden yeni projeler için varsayılan değerdir.

Daha fazla bilgi için bkz. [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**32 bit tercih et**

**Prefer32 bit** onay kutusu işaretliyse, uygulama Windows 'un hem 32-bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışır. Aksi takdirde, uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde 64 bit uygulama olarak çalışır.

64 bitlik bir uygulama olarak çalıştırmak işaretçi boyutunu iki katına çıkarır ve yalnızca 32 bit olan kitaplıklarda uyumluluk sorunlarına neden olabilir. Bir uygulamayı yalnızca önemli ölçüde daha hızlı çalışıyorsa veya 4 GB 'den fazla belleğe ihtiyaç duyduğunda, 64 bit olarak çalıştırmak mantıklı olur.

Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğru olduğunda kullanılabilir:

- **Derle sayfasında**, **hedef CPU** listesi **herhangi bir CPU**olarak ayarlanır.

- Uygulama **sayfasında**, **uygulama türü** listesi projenin bir uygulama olduğunu belirtir.

- **Uygulama sayfasında**, **hedef çerçeve** listesi 4,5 .NET Framework belirtir.

**Uyarı konfigürasyonları**

Bu tabloda, derleme koşulları ve ilgili bildirim düzeyi **yok**, **Uyarı**veya her biri için **hata** listelenmektedir.

Varsayılan olarak, derleme sırasında tüm derleyici uyarıları Görev Listesi eklenir. Derleyicinin uyarı veya hata vermesine yol açmamasını sağlamak için **tüm uyarıları devre dışı bırak** ' ı seçin. Derleyicinin uyarıları düzeltilmesi gereken hata olarak görmesini istiyorsanız, **tüm uyarıları hata olarak değerlendir** ' i seçin.

**Tüm uyarıları devre dışı bırak**

Derleyicinin bu belgede daha önce açıklanan **koşul ve bildirim** tablosunda belirtilen bildirimleri vermesine izin verilip verilmeyeceğini belirtir. Varsayılan olarak, bu onay kutusu temizlenir. Derleyicinin uyarı veya hata vermesine izin vermesini istemek için bu onay kutusunu seçin.

Bu ayar, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) derleyici seçeneğine karşılık gelir.

**Tüm uyarıları hata olarak değerlendir**

Uyarıların nasıl ele alınacağını belirtir. Varsayılan olarak, bu onay kutusu temizlenir, böylece tüm uyarı bildirimleri **Uyarı**olarak ayarlanır. Tüm uyarı bildirimlerini **hata**olarak değiştirmek için bu onay kutusunu işaretleyin.

Bu seçenek yalnızca **tüm uyarıları devre dışı bırak** silinirse kullanılabilir.

**XML belge dosyası oluştur**

Belge bilgilerinin oluşturulup oluşturulmayacağını belirtir. Varsayılan olarak, bu onay kutusu seçilidir ve derleyici belge bilgilerini oluşturup bir XML dosyasına dahil eder. Derleyicinin belge oluşturmamasını istemek için bu onay kutusunu temizleyin.

Bu ayar [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) derleyici seçeneğine karşılık gelir.

**COM birlikte çalışması için kaydolun**

Yönetilen uygulamanızın, bir com nesnesinin uygulamayla etkileşime geçmesini sağlayan bir COM nesnesi (COM çağrılabilir sarmalayıcı) sergileip sunulmayacağını belirtir.

Varsayılan olarak, bu onay kutusu temizlenir ve uygulamanın COM birlikte çalışabilirliğine izin vermemesi gerektiğini belirtir. COM birlikte çalışabilirliğine izin vermek için bu onay kutusunu seçin.

Bu seçenek Windows uygulaması veya konsol uygulaması projeleri için kullanılamaz.

**Derleme olayları**

**Derleme olayları** iletişim kutusuna erişmek için bu düğmeye tıklayın. Proje için oluşturma öncesi ve derleme sonrası yapılandırma yönergelerini belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir. Daha fazla bilgi için bkz. [derleme olayları Iletişim kutusu (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Gelişmiş derleme seçenekleri**

**Advancedderleyici ayarları** iletişim kutusuna erişmek için bu düğmeye tıklayın. Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için **Advancedcompiler ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic projelerine yöneliktir. Daha fazla bilgi için bkz. [Gelişmiş derleyici ayarları Iletişim kutusu (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Derleme Olayları Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)