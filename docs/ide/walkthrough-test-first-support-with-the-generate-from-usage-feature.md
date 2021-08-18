---
title: Kullanımdan Oluştur ile ilk geliştirmeyi test edin
description: Kullanımdan Oluştur özelliğini kullanarak Test-first geliştirme yaklaşımını nasıl dahil etmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/09/2017
dev_langs:
- VB
- CSharp
ms.topic: how-to
helpviewer_keywords:
- Generate From Usage
- Test-First Development
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 323d8c68f55b1804aee20298a2e4c1d34cd9a6e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048368"
---
# <a name="walkthrough-test-first-development-with-the-generate-from-usage-feature"></a>Adım adım kılavuz: Kullanımdan Oluştur özelliğiyle ilk geliştirmeyi test edin

Bu konu başlığında, test öncesi [geliştirmeyi destekleyen](../ide/visual-csharp-intellisense.md#generate-from-usage) Kullanımdan Oluştur özelliğinin nasıl kullanımı gösterebilirsiniz.

 *Test-ilk geliştirme,* yazılım tasarımına, önce ürün belirtimlerine göre birim testleri yazıp ardından testleri başarılı yapmak için gereken kaynak kodu yazarak bir yaklaşımdır. Visual Studio, tanımlanmamış test çalışmalarında ilk kez başvurarak kaynak kodda yeni türler ve üyeler oluşturarak test öncesi geliştirmeyi destekler.

Visual Studio iş akışınız çok az kesintiyle yeni türler ve üyeler üretir. Geçerli konumunu kodda bırakmadan türler, yöntemler, özellikler, alanlar veya oluşturucular için saplamalar oluşturabilirsiniz. Tür oluşturma seçeneklerini belirtmek için bir iletişim kutusu açsanız, iletişim kutusu kapanıyorsa odak hemen geçerli açık dosyaya döner.

Kullanımdan **Oluştur özelliği,** verilerle tümleştirilmiş test çerçeveleriyle Visual Studio. Bu konu başlığında, Microsoft Birim Testi Çerçevesi açıklanmıştır.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="create-a-windows-class-library-project-and-a-test-project"></a>Windows Sınıf Kitaplığı projesi ve Test projesi oluşturma

1. C# veya Visual Basic sınıf kitaplığı **projesinde yeni Windows oluşturun.** Kullandığınız `GFUDemo_VB` dile `GFUDemo_CS` bağlı olarak veya adını girin.

2. Bu **Çözüm Gezgini** üst köşesindeki çözüm simgesine sağ tıklayın ve Yeni Ekle'yi **Project.**  >  

3. Yeni bir Birim **Testi Project (.NET Framework) projesi** oluşturun.

   ::: moniker range="vs-2017"

   Aşağıdaki çizimde, C# **Project** yeni özellikler iletişim kutusu gösterilmiştir.

   ![Birim Testi Project şablonu](../ide/media/newproject_test.png)

   ::: moniker-end

### <a name="add-a-reference-to-the-class-library-project"></a>Sınıf Kitaplığı projesine başvuru ekleme

1. Bu **Çözüm Gezgini,** birim testi projenizin altında Başvurular **girdisini sağ tıklatın ve** Başvuru Ekle'yi **seçin.**

2. Başvuru Yöneticisi **iletişim** kutusunda Projeler'i **ve** ardından sınıf kitaplığı projesini seçin.

3. Başvuru **Yöneticisi** iletişim kutusunu kapatmak **için Tamam'ı** seçin.

4. Çözümlerinizi kaydedin. Artık testleri yazmaya başlamaya hazır oluruz.

### <a name="generate-a-new-class-from-a-unit-test"></a>Birim testinde yeni bir sınıf oluşturma

1. Test projesi *UnitTest1* adlı bir dosya içerir. Kod düzenleyicisinde açmak **Çözüm Gezgini** bu dosyaya çift tıklayın. Bir test sınıfı ve test yöntemi oluşturulmuş.

2. sınıf bildirimini bulun ve `UnitTest1` olarak yeniden adlandıryın. `AutomobileTest`

   > [!NOTE]
   > IntelliSense artık IntelliSense deyimi tamamlama için iki alternatif sağlar: *tamamlama modu* ve *öneri modu.* Sınıfların ve üyelerin tanımlanmadan önce kullanıldıkları durumlar için öneri modunu kullanın. Bir **IntelliSense penceresi** açık olduğunda, tamamlama modu ile öneri modu arasında geçiş yapmak için **Ctrl** + **Alt** +  Ara Çubuğuna basabilirsiniz. Daha [fazla bilgi için bkz. IntelliSense](../ide/using-intellisense.md) kullanma. Öneri modu, bir sonraki adımda yazarken `Automobile` size yardımcı olur.

3. yöntemini bulun `TestMethod1()` ve olarak yeniden adlandıryın. `DefaultAutomobileIsInitializedCorrectly()` Bu yöntemin içinde, aşağıdaki ekran görüntülerde gösterildiği gibi `Automobile` adlı yeni bir sınıf örneği oluşturun. Derleme zamanı hatasını gösteren dalgalı bir alt çizgi [](../ide/quick-actions.md) görüntülenir ve sol kenar boşluğunda veya üzerine gelirsiniz dalgalı çizginin hemen altında Hızlı Eylemler hata ampulü görünür.

    ![Visual Basic'de Hızlı Eylemler](../ide/media/genclass_underlinevb.png)

    ![C'de Hızlı Eylemler&#35;](../ide/media/genclass_underline.png)

4. Hızlı Eylemler **ampulü seçin veya** tıklayın. Türün tanımlanmamış olduğunu bir hata `Automobile` iletisiyle karşılarsınız. Ayrıca bazı çözümler de sunulmaktadır.

5. Tür **Oluştur iletişim kutusunu** açmak için Yeni tür **oluştur'a** tıklayın. Bu iletişim kutusu, türü farklı bir projede oluşturma gibi seçenekler sağlar.

6. Dosya **Project** **GFUDemo \_ VB'ye** tıklayın **veya GFUDemo_CS'a** dosyayı test projesi Visual Studio sınıf kitaplığı projesine eklemesini talimat olarak ekleyin. Henüz seçilmemişse Yeni dosya oluştur'ı **seçin ve** Automobile.cs veya *Automobile.vb* *olarak ad girin.*

     ![Yeni Tür Oluştur iletişim kutusu](../ide/media/genotherdialog.png)

7. İletişim **kutusunu** kapatmak ve yeni dosyayı oluşturmak için Tamam'a tıklayın.

8. Yeni **Çözüm Gezgini** *Automobile.vb* **veya** *Automobile.cs* dosyasının **orada olduğunu doğrulamak** için GFUDemo_VB veya GFUDemo_CS proje düğümünün altına bakın. Kod düzenleyicisinde odak hala içindedir ve bu sayede testlerinizi en az `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` kesintiyle yazmaya devam edebilirsiniz.

### <a name="generate-a-property-stub"></a>Özellik saplama oluşturma
Ürün belirtimleri sınıfının ve adlı `Automobile` iki genel özelliği olduğunu ifade ediyor `Model` `TopSpeed` olabilir. Bu özellikler varsayılan ve değerleriyle varsayılan `"Not specified"` oluşturucu `-1` tarafından başlatmalıdır. Aşağıdaki birim testi, varsayılan oluşturucun özellikleri doğru varsayılan değerlerine ayara sahip olduğunu doğrular.

1. Aşağıdaki kod satırı test `DefaultAutomobileIsInitializedCorrectly` yöntemine ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet1":::

2. Kod, üzerinde tanımlanmamış iki özelense ve `Automobile` altında dalgalı bir alt çizgi `Model` `TopSpeed` görünür. Üzerine gelin `Model` ve Hızlı Eylemler hata **ampulü'ne** ve ardından **'Automobile.Model' özelliğini oluştur'a seçin.**

3. Özelliği için aynı şekilde bir `TopSpeed` özellik saplama oluşturma.

     sınıfında, `Automobile` yeni özelliklerin türleri bağlamdan doğru şekilde alıtır.

### <a name="generate-a-stub-for-a-new-constructor"></a>Yeni oluşturucu için saplama oluşturma
Şimdi ve özelliklerini başlatmak için bir oluşturucu saplama oluşturan bir test yöntemi `Model` `TopSpeed` oluşturacak. Daha sonra testi tamamlamak için daha fazla kod eksersiniz.

1. Aşağıdaki ek test yöntemini sınıfınıza `AutomobileTest` ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb" id="Snippet2":::

2. Kırmızı geçiş **altındaki Hızlı** Eylemler hata ampulü'ne ve ardından 'Automobile' içinde **oluşturucu oluştur'a tıklayın.**

     Sınıf dosyasında yeni oluşturucu, oluşturucu çağrısında kullanılan yerel değişkenlerin adlarını inceledi, sınıfta aynı adlara sahip özellikler buldu ve özelliklerinde bağımsız değişken değerlerini depolamak için oluşturucu gövdesinde sağlanan kodu `Automobile` `Automobile` `Model` `TopSpeed` inceledi.

3. Yeni oluşturucuyu oluşturmanın ardından, içinde varsayılan oluşturucuya yapılan çağrının altında dalgalı bir alt çizgi `DefaultAutomobileIsInitializedCorrectly` görünür. Hata iletisi, sınıfın sıfır `Automobile` bağımsız değişken alan bir oluşturucusu olmadığını gösterir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için  Hızlı Eylemler hata ampulü'ne tıklayın ve **ardından 'Automobile' içinde oluşturucu oluştur'a tıklayın.**

### <a name="generate-a-stub-for-a-method"></a>Yöntem için saplama oluşturma
belirtimi, ve özellikleri varsayılan değerlerden farklı bir değere ayarlanmışsa yeni bir `Automobile` `IsRunning` `Model` `TopSpeed` durumuna koyabilirsiniz durumunun olduğunu varsayabilirsiniz.

1. aşağıdaki satırları yöntemine `AutomobileWithModelNameCanStart` ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb" id="Snippet3":::

2. Yöntem çağrısı **için Hızlı Eylemler** hata ampulü'ne ve ardından `myAuto.Start` **'Automobile.Start' yöntemini oluştur'a tıklayın.**

3. özelliği için **Hızlı Eylemler** ampulü'ne ve `IsRunning` ardından **'Automobile.IsRunning' özelliğini oluştur'a tıklayın.**

     sınıfı `Automobile` artık adlı bir yöntemi ve adlı bir özelliği `Start()` `IsRunning` içerir.

### <a name="run-the-tests"></a>Testleri çalıştırma

1. Test menüsünde **Tüm** Testleri   >  **Çalıştır'ı seçin.**

     Tüm   >  **Testleri Çalıştır** komutu, geçerli çözüm için yazılmış tüm test çerçevelerinde tüm testleri çalıştırır. Bu durumda iki test vardır ve ikisi de beklendiği gibi başarısız olur. Koşul `DefaultAutomobileIsInitializedCorrectly` döndür olduğundan test başarısız `Assert.IsTrue` `False` olur. sınıfındaki `AutomobileWithModelNameCanStart` yöntemi bir özel durum oluşturur çünkü test başarısız `Start` `Automobile` olur.

     Test Sonuçları  penceresi aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png)

2. Test **Test Sonuçları** her test sonucu satırına çift tıklar ve her testin konumunu gösterir.

### <a name="implement-the-source-code"></a>Kaynak kodu uygulama

1. , ve özelliklerinin doğru varsayılan , ve (veya C# için) değerlerine başlatılması için aşağıdaki kodu varsayılan `Model` `TopSpeed` `IsRunning` `"Not specified"` `-1` `False` `false` oluşturucuya ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet5":::

2. yöntemi çağrıldıysa, yalnızca veya özellikleri varsayılan değerlerinden farklı bir değere ayarlanmışsa `Start` `IsRunning` bayrağını true `Model` olarak `TopSpeed` ayarlaması gerekir. yönteminin `NotImplementedException` gövdesinden kaldırın ve aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb" id="Snippet6":::

### <a name="run-the-tests-again"></a>Testleri yeniden çalıştırma

- Test menüsünde **Çalıştır'ın** üzerine **gelin ve** ardından Tüm **Testler'e tıklayın.**

     Bu kez testler geçer. Test Sonuçları  penceresi aşağıdaki çizimde gösterilmiştir.

     ![Geçen test sonuçları](../ide/media/testspassed.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanımdan oluşturma](../ide/visual-csharp-intellisense.md#generate-from-usage)
- [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [IntelliSense kullanma](../ide/using-intellisense.md)
- [Kodunuzu birim testi](../test/unit-test-your-code.md)
- [Hızlı Eylemler](../ide/quick-actions.md)
