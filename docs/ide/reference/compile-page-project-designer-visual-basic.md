---
title: Derleme Sayfası, Proje Tasarımcısı (Visual Basic)
description: Visual Studio ' de derleme yönergelerini belirtmeyi öğrenin. Ayrıca, bu sayfada gelişmiş derleyici seçeneklerini ve derleme öncesi veya derleme sonrası olayları da belirtebilirsiniz.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4142e958bcac56ea972cc271d8b3f9fa215f21ae80b99bc78c95f7109a4f85f8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430583"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)

derleme yönergelerini belirtmek için Project tasarımcısının **derle** sayfasını kullanın. Ayrıca, bu sayfada gelişmiş derleyici seçeneklerini ve derleme öncesi veya derleme sonrası olayları da belirtebilirsiniz.

**Derle** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü ( **çözüm** düğümünü değil) seçin. ardından, menü çubuğunda **Project**, **özellikler** ' i seçin. Project tasarımcı göründüğünde, **derle** sekmesine tıklayın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve platform

Aşağıdaki ayarlar, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

> [!NOTE]
> Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. Bu nedenle, **yapılandırma** ve **Platform** listeleri görüntülenmez.

**Yapılandırma**

Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın** veya **Tüm yapılandırmalardan** yapılır. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../../ide/understanding-build-configurations.md) ve [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

**Platform**

Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. **Herhangi BIR CPU** (varsayılan), **x64** veya **x86** belirtebilirsiniz.

## <a name="compiler-configuration-options"></a>Derleyici yapılandırma seçenekleri

Aşağıdaki ayarlar, derleyici yapılandırma seçeneklerini ayarlamanıza olanak sağlar.

**Derleme çıkış yolu**

Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Derleme çıktısının yolunu bu kutuya yazın veya bir yol seçmek için, **Gözden** geçirme düğmesine tıklayın. Yolun göreli olduğunu unutmayın; mutlak bir yol girerseniz, göreli olarak kaydedilir. Varsayılan yol bin\Debug\ veya bin\Release ' dir \\ .

Basitleştirilmiş derleme yapılandırmalarında, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata ayıklama** menüsündeki **derleme** komutu (F5), belirttiğiniz **çıkış yolundan** bağımsız olarak derlemeyi hata ayıklama konumuna koyar. Ancak, **Yapı** menüsündeki **Build** komutu onu belirttiğiniz konuma koyar.

**Seçenek açık**

Değişkenlerin örtük bildirimine izin verilip verilmeyeceğini belirtir. Değişkenlerin açık bildirimini gerektirmek için **Açık '** ı seçin. Bu, değişkenlerin kullanılmadan önce bildirilmemiş olması durumunda derleyicinin hata raporlamasına neden olur. Örtük değişken bildirimine izin vermek için **kapalı** ' yı seçin.

Bu ayar [/OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası [açık bir seçenek](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **Açık ayar seçeneğini** geçersiz kılar.

Yeni bir proje oluşturduğunuzda, **derleme sayfasındaki** **Açık ayar seçeneği** , **Seçenekler** iletişim kutusundaki **Açık seçenek** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Açık seçenek** olan ilk varsayılan ayar **açıktır**.

**Seçeneğinin açık** olarak ayarlanması `Off` , genellikle iyi bir uygulamadır. Bir veya daha fazla konumda değişken adı yanlış yazdığınızda, program çalıştırıldığında beklenmedik sonuçlara neden olabilir.

**Option Strict**

Katı tür semantiğinin zorlanıp zorlanmayacağını belirtir. **Option Strict** **Açık** olduğunda, aşağıdaki koşullar derleme zamanı hatasına neden olur:

- Örtük daraltma dönüşümleri

- Geç bağlama

- Bir tür ile sonuçlanan örtük yazma `Object`

Örtük daraltma dönüştürme hataları, daraltma dönüştürmesi olan bir örtük veri türü dönüştürmesi olduğunda oluşur. Daha fazla bilgi için bkz. [Option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [örtük ve açık dönüştürmeler](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), [genişletme ve daraltma dönüştürmeleri](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Bir nesne, tür olarak belirtilen bir özelliğin veya yöntemin bir özelliğine atandığında geç bağlanır `Object` . Daha fazla bilgi için bkz. [Option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement) yanı sıra [erken ve geç bağlama](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Örtük nesne türü hataları, tanımlı bir değişken için uygun bir tür çıkarsanmadığında oluşur, bu nedenle bir türü `Object` algılanır. Bu öncelikle `Dim` , bir yan tümce kullanmadan bir değişkeni bildirmek için bir deyimi kullandığınızda oluşur `As` ve `Option Infer` kapalı olur. daha fazla bilgi için bkz. [option Strict deyimin](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [option ınfer deyimleri](/dotnet/visual-basic/language-reference/statements/option-infer-statement)ve [Visual Basic Language belirtimi](/dotnet/visual-basic/reference/language-specification).

**Katı ayarı seçeneği** , [/OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [Option Strict ifadesini](/dotnet/visual-basic/language-reference/statements/option-strict-statement)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **katı** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **katı** ayarı **Seçenekler** iletişim kutusundaki **katı ayar seçeneğinin** değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içinde **Strict seçeneğinin** ilk varsayılan ayarı **kapalıdır**.

**İsteğe bağımsız kesin uyarılar**

**Derleme sayfasının** **Uyarı yapılandırması** bölümü, açık olduğunda derleme zamanı hatasına neden olan üç koşula karşılık gelen ayarlara sahiptir `Option Strict` . Aşağıdaki ayarlar şunlardır:

- **Örtük dönüştürme**

- **Geç bağlama; çağrı çalışma zamanında başarısız olabilir**

- **Örtük tür; nesne varsayıldı**

**Option Strict** **on on** olarak ayarlandığında, bu uyarı yapılandırma ayarlarının üçü de **hata** olarak ayarlanır. **Option Strict** ' i **off** olarak ayarlarsanız, üç ayar **hiçbiri None** olarak ayarlanır.

Her uyarı yapılandırma ayarını **hiçbiri**, **Uyarı** veya **hata** olarak tek tek değiştirebilirsiniz. Üç uyarı yapılandırma ayarı **hata** olarak ayarlanırsa, `On` `Option strict` kutusunda görünür. Üçü de **hiçbiri** olarak ayarlandıysa, `Off` Bu kutuda görüntülenir. Bu ayarların diğer birleşimleri için **(özel)** görüntülenir.

**Option Compare**

Kullanılacak dize karşılaştırmasının türünü belirtir. Derleyicinin ikili, büyük/küçük harfe duyarlı dize karşılaştırmaları kullanmasını söylemek için **binary** ' ı seçin. Yerel ayara özgü, büyük/küçük harfe duyarsız metin dizesi karşılaştırmaları kullanmak için **metin** seçin.

Bu ayar [/OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [Seçenek karşılaştırma ekstresi](/dotnet/visual-basic/language-reference/statements/option-compare-statement)içeriyorsa, `Binary` `Text` deyimdeki or değeri, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **Seçenek karşılaştırma** ayarı, **Seçenekler** iletişim kutusundaki **Seçenek karşılaştırma** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb Varsayılanları** Içindeki **Option Compare** 'In ilk varsayılan ayarı **binary**'dir.

**Seçenek çıkarımı**

Değişken bildirimlerinde yerel tür çıkarımını izin verilip verilmeyeceğini belirtir. Yerel tür çıkarımı kullanımına izin vermek için **Açık '** ı seçin. Yerel tür çıkarımı engellemek için **kapalı** ' yı seçin.

Bu ayar [/OptionInfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) derleyici seçeneğine karşılık gelir.

Bir kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](/dotnet/visual-basic/language-reference/statements/option-infer-statement)içeriyorsa, `On` `Off` deyimdeki or değeri, **derleme sayfasındaki** **seçenek çıkarımı** ayarını geçersiz kılar.

Bir proje oluşturduğunuzda, **derleme sayfasındaki** **seçenek çıkarımı** ayarı **Seçenekler** iletişim kutusundaki **seçenek çıkarımı** ayarı değerine ayarlanır. Bu iletişim kutusundaki ayarı görüntülemek veya değiştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın. **Vb** varsayılan olarak **seçenek çıkarımı** başlangıç varsayılan ayarı **Açık** olur.

**Hedef CPU**

Çıkış dosyası tarafından hedeflenen işlemciyi belirtir. Her türlü 32 bit Intel uyumlu işlemci için **x86** , her türlü 64 bit Intel uyumlu işlemci için **x64** , herhangi bir ARM işlemcisi için **ARM** veya herhangi bir Işlemcinin kabul EDILEBILIR olduğunu belirtmek için **herhangi bir CPU** belirleyin. **Tüm CPU** , uygulamanın en çok sayıda donanım türünde çalışmasına izin verdiğinden yeni projeler için varsayılan değerdir.

Daha fazla bilgi için bkz. [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**32 bit tercih et**

**Prefer32-bit** onay kutusu seçiliyse, uygulama hem 32 bit hem de 64 bit uygulamanın 32 bitlik sürümlerinde 32 bitlik bir uygulama Windows. Aksi takdirde, uygulama Windows'nin 32 bit sürümlerinde 32 bit uygulama olarak ve Windows'nin 64 bit sürümlerinde 64 bit uygulama olarak Windows.

64 bit uygulama olarak çalıştırarak işaretçi boyutu iki katına çıkar ve yalnızca 32 bit kitaplıklarla uyumluluk sorunlarına neden olabilir. Yalnızca önemli ölçüde daha hızlı çalışan veya 4 GB'den fazla belleğe ihtiyacı olan bir uygulamayı 64 bit olarak çalıştırmak mantıklıdır.

Bu onay kutusu yalnızca aşağıdaki koşulların hepsi doğruysa kullanılabilir:

- Derleme **Sayfasında Hedef** **CPU** listesi Herhangi bir **CPU olarak ayarlanır.**

- Uygulama **Sayfasında,** Uygulama **türü listesi** projenin bir uygulama olduğunu belirtir.

- Uygulama **Sayfasında,** Hedef **çerçeve listesi** 4.5 .NET Framework belirtir.

**Uyarı yapılandırmaları**

Bu tabloda derleme koşulları ve her biri için yok, **Uyarı** veya **Hata bildirim** **düzeyi** listelemektedir.

Varsayılan olarak, derleme sırasında tüm derleyici uyarıları Görev Listesi eklenir. Derleyiciye **uyarı veya hata** çıkarmaması için Tüm uyarıları devre dışı bırak'ı seçin. Derleyicinin **uyarıları düzeltilecek hatalar** olarak davranması için Tüm uyarıları hata olarak davran'ı seçin.

**Tüm uyarıları devre dışı bırak**

Derleyicinin bu belgenin önceki sürümlerinde açıklanan Koşul ve Bildirim tablosunda belirtildiği gibi bildirim **vermesine** izin verip vermey kararlarını belirtir. Varsayılan olarak bu onay kutusu işaretli değildir. Derleyiciye uyarı veya hata açmaması talimatı için bu onay kutusunu seçin.

Bu ayar [/nowarn derleyici seçeneğine](/dotnet/visual-basic/reference/command-line-compiler/nowarn) karşılık gelen bir ayardır.

**Tüm uyarıları hata olarak davran**

Uyarıların nasıl işlen olduğunu belirtir. Varsayılan olarak, bu onay kutusu temizdir, böylece tüm uyarı bildirimleri Uyarı olarak **kalır.** Tüm uyarı bildirimlerini Hata olarak değiştirmek için bu onay kutusunu **seçin.**

Bu seçenek yalnızca Tüm uyarıları **devre dışı bırak seçeneği temizse** kullanılabilir.

**XML belge dosyası oluşturma**

Belge bilgileri oluşturulıp oluşturul olmadığını belirtir. Varsayılan olarak, bu onay kutusu seçilidir ve derleyiciye belge bilgileri oluşturması ve bir XML dosyasına dahil etmelerini sağlar. Derleyiciye belge oluşturmaması talimatı için bu onay kutusunu temizleyin.

Bu ayar /doc derleyici [seçeneğine](/dotnet/visual-basic/reference/command-line-compiler/doc) karşılık gelen bir ayardır.

**COM birlikte çalışma için kaydolma**

Yönetilen uygulamanın bir COM nesnesinin uygulamayla etkileşim kurmasını sağlayan bir COM nesnesini (COM çağrılabilir sarmalayıcı) ortaya çıkarıp ortaya çıkarmayacaklarını belirtir.

Varsayılan olarak, uygulamanın COM birlikte çalışmasına izin ver vermayacaklarını belirten bu onay kutusu temizdir. COM birlikte çalışmasına izin vermek için bu onay kutusunu seçin.

Bu seçenek, uygulama Windows Konsol Uygulaması projelerinde kullanılamaz.

**Derleme Olayları**

Derleme Olayları iletişim kutusuna erişmek **için bu düğmeye** tıklayın. Proje için derleme öncesi ve derleme sonrası yapılandırma yönergelerini belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic için geçerlidir. Daha fazla bilgi için [bkz. Derleme Olayları İletişim Kutusu (Visual Basic).](../../ide/reference/build-events-dialog-box-visual-basic.md)

**Gelişmiş Derleme Seçenekleri**

**AdvancedCompiler** Ayarlar iletişim kutusuna erişmek için bu düğmeye tıklayın. Bir projenin gelişmiş derleme Ayarlar belirtmek için **AdvancedCompiler** Ayarlar iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca Visual Basic için geçerlidir. Daha fazla bilgi için [bkz. Gelişmiş Derleyici Ayarlar İletişim Kutusu (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic Command-Line Derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)
