---
title: 'İzlenecek yol: kullanımdan oluştur özelliğinden önce test desteği | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f40ed5f3070f177d1c914495f78a223364d64ae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662672"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>İzlenecek Yol: Kullanımdan Üret Özelliği ile Önce Test Desteği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, test-ilk geliştirmeyi destekleyen [kullanım dışı oluşturma](../misc/generate-from-usage.md) özelliğinin nasıl kullanılacağı gösterilmektedir.

 *Test-ilk geliştirme* , ürün belirtimlerine göre birim testlerini ilk kez yazacağınız ve sonra testlerin başarılı olması için gereken kaynak kodu yazdığınız yazılım tasarımına yönelik bir yaklaşımdır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , tanımlanmadan önce test çalışmalarınıza ilk kez başvurduğunuzda, kaynak kodda yeni türler ve Üyeler oluşturarak test-ilk geliştirmeyi destekler.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] iş akışınız için en az kesintiyle yeni türler ve Üyeler üretir. Türler, Yöntemler, özellikler, alanlar veya oluşturucular için kod içinde geçerli konumunuzu bırakmadan, saplamalar oluşturabilirsiniz. Tür oluşturma seçeneklerini belirtmek için bir iletişim kutusu açtığınızda, odak iletişim kutusu kapandığında geçerli açık dosyaya hemen döner.

 Kullanımdan Oluştur özelliği ile tümleştirilen test çerçeveleri ile birlikte kullanılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu konuda, Microsoft birim testi çerçevesi gösterilmiştir.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Bir Windows sınıf kitaplığı projesi ve bir test projesi oluşturmak için

1. [!INCLUDE[csprcs](../includes/csprcs-md.md)]Veya içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Yeni bir Windows sınıf kitaplığı projesi oluşturun. `GFUDemo_VB` `GFUDemo_CS` Kullandığınız dile bağlı olarak veya olarak adlandırın.

2. **Çözüm Gezgini**, üstteki çözüm simgesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın. **Yeni proje** iletişim kutusunda, sol taraftaki **Proje türleri** bölmesinde **Test**' e tıklayın.

3. **Şablonlar** bölmesinde, **birim testi projesi** ' ne tıklayın ve varsayılan UnitTestProject1 adını kabul edin. Aşağıdaki çizim, içinde göründüğü zaman iletişim kutusunu gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] . İçinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] iletişim kutusu benzer şekilde görünür.

     ![Yeni test projesi iletişim kutusu](../ide/media/newproject-test.png "NewProject_Test") Yeni proje iletişim kutusu

4. **Yeni proje** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. Sınıf projenizde, **Çözüm Gezgini**, **Başvurular** girişine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

6. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** ' i seçin ve ardından birim testi projenizi seçin.

7. **Tamam** ' a tıklayarak **başvuru Yöneticisi** iletişim kutusunu kapatın.

8. **Class1** dosyasında, var olan **using** deyimlerinin son öğesinden hemen sonra, test projesi için bir **using** deyimi ekleyin:

    * Visual Basic, Ekle `Using UnitTestProject1`

    * C# dilinde, Ekle `using UnitTestProject1;`

9. Çözümünüzü kaydedin. Artık testleri yazmaya başlamaya hazırsınız

### <a name="to-generate-a-new-class-from-a-unit-test"></a>Birim testten yeni bir sınıf oluşturmak için

1. Test projesi UnitTest1 adlı bir dosya içerir. Kod düzenleyicisinde açmak için **Çözüm Gezgini** bu dosyaya çift tıklayın. Test sınıfı ve test yöntemi üretildi.

2. Sınıfının bildirimini bulun `UnitTest1` ve olarak yeniden adlandırın `AutomobileTest` . C# ' de bir `UnitTest1()` Oluşturucu varsa, olarak yeniden adlandırın `AutomobileTest()` .

    > [!NOTE]
    > IntelliSense artık IntelliSense deyimin tamamlanması için iki alternatif sağlıyor: *tamamlama modu* ve *öneri modu*. Sınıfların ve üyelerin tanımlanmadan önce kullanıldığı durumlar için öneri modunu kullanın. Bir IntelliSense penceresi açıkken, tamamlama modu ve öneri modu arasında geçiş yapmak için CTRL + ALT + ara çubuğu tuşlarına basabilirsiniz. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md) . Öneri modu, bir sonraki adımda yazarken yardımcı olur `Automobile` .

3. Yöntemini bulun `TestMethod1()` ve olarak yeniden adlandırın `DefaultAutomobileIsInitializedCorrectly()` . Bu yöntemin içinde, `Automobile` Aşağıdaki çizimlerde gösterildiği gibi adlı bir sınıfın yeni bir örneğini oluşturun. Bir derleme zamanı hatası gösteren dalgalı alt çizgi görünür ve tür adı altında akıllı etiket görüntülenir. Akıllı etiketin tam konumu, veya kullanıyor olmanıza bağlı olarak değişir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] .

     ![Visual Basic akıllı etiket altı çizili](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB") Visual Basic

     ![C&#35;akıllı etiket altı çizili ](../ide/media/genclass-underline.png "GenClass_Underline") Visual C #

4. Henüz adlandırılmış hiçbir tür tanımlanmadığı belirten bir hata iletisi görmek için fare işaretçisini akıllı etiketin üzerine getirin `Automobile` . Akıllı etikete tıklayın veya CTRL + tuşlarına basın. (CTRL + Period) Aşağıdaki çizimlerde gösterildiği gibi, kullanımdan oluştur kısayol menüsünü açmak için.

     ![Visual Basic 'de akıllı etiket bağlam menüsü](../ide/media/genclass-smartvb.png "GenClass_SmartVB") Visual Basic

     ![C&#35;'de akıllı etiket bağlam menüsü ](../ide/media/genclass-smartcs.png "GenClass_SmartCS") Visual C #

5. Artık iki seçeneğiniz vardır. Test projenizde yeni bir dosya oluşturmak ve adlı boş bir sınıf ile doldurmak için **' class otomobil ' oluştur** ' a tıklayabilirsiniz `Automobile` . Bu, geçerli projede varsayılan erişim değiştiricilerine sahip yeni bir dosyada yeni bir sınıf oluşturmanın hızlı bir yoludur. Yeni tür **Oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a de tıklayabilirsiniz. Bu, sınıfı varolan bir dosyaya yerleştirmeyi ve dosyayı başka bir projeye eklemeyi içeren seçenekler sağlar.

     Aşağıdaki çizimde gösterilen **yeni tür oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a tıklayın. **Proje** listesinde, test projesi yerine **GFUDemo_VB** **GFUDemo_CS** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dosyayı kaynak kodu projesine eklemeyi söylemek için GFUDemo_VB veya GFUDemo_CS ' a tıklayın.

     ![Yeni tür oluştur iletişim kutusu](../ide/media/genotherdialog.png "Genotheriletişim kutusu") Yeni tür oluştur iletişim kutusu

6. İletişim kutusunu kapatmak ve yeni dosyayı oluşturmak için **Tamam** ' ı tıklatın.

7. **Çözüm Gezgini**, yeni otomobil. VB veya automobile.cs dosyasının orada olduğunu doğrulamak için, GFUDemo_VB veya GFUDemo_CS proje düğümüne bakın. Kod düzenleyicisinde, odak hala devam etmektedir `AutomobileTest.DefaultAutomobileIsInitializedCorrectly` . Testinizi en az kesintiye göre yazmaya devam edebilirsiniz.

### <a name="to-generate-a-property-stub"></a>Bir özellik saplaması oluşturmak için

1. Ürün belirtiminin, `Automobile` sınıfının ve adında iki ortak özelliğe sahip olduğunu varsayalım `Model` `TopSpeed` . Bu özelliklerin varsayılan ve varsayılan oluşturucularla başlatılması gerekir `"Not specified"` `-1` . Aşağıdaki birim testi varsayılan oluşturucunun özellikleri doğru varsayılan değerlerine ayarladiğini doğrular.

     Aşağıdaki kod satırını öğesine ekleyin `DefaultAutomobileIsInitializedCorrectly` .

     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]

     Kod, üzerinde iki tanımsız özelliğe başvurduğundan `Automobile` , akıllı bir etiket görünür. Akıllı etiketine tıklayın `Model` ve sonra **özellik saplaması oluştur**' a tıklayın. Özelliği için de özellik saplaması oluşturun `TopSpeed` .

     `Automobile`Sınıfında, yeni özelliklerin türleri içerikten doğru şekilde algılanır.

     Aşağıdaki çizimde akıllı etiket kısayol menüsü gösterilmektedir.

     ![Visual Basic özellik bağlam menüsü oluştur](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB") Visual Basic

     ![C&#35;özellik bağlam menüsü oluştur ](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS") Visual C #

### <a name="to-locate-the-source-code"></a>Kaynak kodunu bulmak için

1. Yeni özelliklerin oluşturulduğunu doğrulayabilmeniz için Automobile.cs veya otomobil. vb kaynak kodu dosyasına gitmek üzere **Git** özelliğini kullanın.

     **Git** özelliği, bir metin dizesini bir tür adı veya bir adın parçası gibi hızlıca girmenizi sağlar ve sonuç listesindeki öğesine tıklayarak istediğiniz konuma gidebilirsiniz.

     Kod düzenleyicisine tıklayıp CTRL +, (CTRL + virgül) tuşlarına basarak **şuraya git** iletişim kutusunu açın. Metin kutusuna yazın `automobile` . Listeden **otomobil** ' ye tıklayın ve ardından **Tamam**' a tıklayın.

     Aşağıdaki çizimde, penceresine **Git** penceresi gösterilmiştir.

     ![İletişim kutusuna git](../ide/media/navigate-2.png "Navigate_2") Pencereye git

### <a name="to-generate-a-stub-for-a-new-constructor"></a>Yeni bir Oluşturucu için bir saplama oluşturmak için

1. Bu test yönteminde, `Model` ve `TopSpeed` özelliklerini, belirttiğiniz değerlere sahip olacak şekilde başlatacak bir Oluşturucu saplaması oluşturacaksınız. Daha sonra, testi tamamlamaya daha fazla kod ekleyeceksiniz. Aşağıdaki ek test yöntemini `AutomobileTest` sınıfınıza ekleyin.

     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]

2. Yeni sınıf oluşturucusunun altındaki akıllı etikete tıklayın ve sonra **Oluşturucu saplama oluştur**' a tıklayın. `Automobile`Sınıf dosyasında, yeni oluşturucunun Oluşturucu çağrısında kullanılan yerel değişkenlerin adlarını incelediğine, sınıfta aynı adlara sahip olan özelliklerin bulunduğunu `Automobile` ve bağımsız değişken değerlerini ve özelliklerinde depolamak için Oluşturucu gövdesinde sağlanan kodu içerdiğine dikkat edin `Model` `TopSpeed` . ( [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ' De, `_model` `_topSpeed` Yeni oluşturucudaki ve alanları, ve özellikleri için örtük olarak tanımlanmış yedekleme alanlarıdır `Model` `TopSpeed` .)

3. Yeni oluşturucuyu oluşturduktan sonra, içindeki varsayılan oluşturucuya yapılan çağrının altında dalgalı bir alt çizgi görünür `DefaultAutomobileIsInitializedCorrectly` . Hata iletisi, `Automobile` sınıfın sıfır bağımsız değişken alan bir Oluşturucusu olmadığını belirtir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için akıllı etikete tıklayın ve sonra **Oluşturucu saplama oluştur**' a tıklayın.

### <a name="to-generate-a-stub-for-a-method"></a>Bir yöntem için saplama oluşturmak için

1. Belirtiminin, `Automobile` `Model` ve `TopSpeed` özellikleri varsayılan değerlerden başka bir şeye ayarlandıysa, çalışma durumuna yeni bir şekilde yerleştirileceğini belirten belirtim olduğunu varsayalım. Yöntemine aşağıdaki satırları ekleyin `AutomobileWithModelNameCanStart` .

     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]

2. Yöntem çağrısının akıllı etiketine tıklayın `myAuto.Start` ve ardından **Yöntem saplaması oluştur**' a tıklayın.

3. Özelliğin akıllı etiketine tıklayın `IsRunning` ve sonra **özellik saplaması oluştur**' a tıklayın. `Automobile`Sınıfı artık aşağıdaki kodu içerir.

     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]

### <a name="to-run-the-tests"></a>Testleri çalıştırmak için

1. **Birim testi** menüsünde, **birim testlerini Çalıştır**' ın üzerine gelin ve ardından **tüm sınamalar**' ı tıklatın. Bu komut, geçerli çözüm için yazılan tüm test çerçevelerinden tüm testleri çalıştırır.

     Bu durumda, iki test vardır ve beklendiği gibi her ikisi de başarısız olur. `DefaultAutomobileIsInitializedCorrectly`Koşul döndürdüğü için test başarısız olur `Assert.IsTrue` `False` . `AutomobileWithModelNameCanStart` `Start` `Automobile` Sınıftaki yöntem bir özel durum oluşturduğundan test başarısız olur.

     **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png "TestsFailed") Test Sonuçları penceresi

2. **Test sonuçları** penceresinde, her test hatasının konumuna gitmek için her test sonucu satırına çift tıklayın.

### <a name="to-implement-the-source-code"></a>Kaynak kodu uygulamak için

1. Aşağıdaki kodu varsayılan oluşturucuya ekleyerek `Model` , `TopSpeed` ve `IsRunning` özelliklerinin tamamı,, ve `"Not specified"` `-1` `True` () doğru varsayılan değerlerine başlatılır `true` .

     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]

2. `Start`Yöntemi çağrıldığında, `IsRunning` bayrağı true olarak ayarlamanız gerekir, `Model` Aksi takdirde veya `TopSpeed` özellikleri varsayılan değerleri dışında bir değere ayarlanır. `NotImplementedException`Yöntemini Yöntem gövdesinden kaldırın ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]

### <a name="to-run-the-tests-again"></a>Testleri yeniden çalıştırmak için

1. **Test** menüsünde, **Çalıştır**' ın üzerine gelin ve ardından **Çözümdeki tüm testler**' e tıklayın. Testlerin geçişi bu kez yapılır. **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Geçilen test sonuçları](../ide/media/testspassed.png "Testsgeçti") Test Sonuçları penceresi

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense birimini kullanarak](../ide/using-intellisense.md) [kullanım](../misc/generate-from-usage.md) [yazma kodundan](../ide/writing-code-in-the-code-and-text-editor.md) oluşturma [kodunuzu test](../test/unit-test-your-code.md) etme
