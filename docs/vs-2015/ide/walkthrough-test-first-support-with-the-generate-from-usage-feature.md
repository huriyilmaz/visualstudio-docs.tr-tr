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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662672"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>İzlenecek Yol: Kullanımdan Üret Özelliği ile Önce Test Desteği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, test-ilk geliştirmeyi destekleyen [kullanım dışı oluşturma](../misc/generate-from-usage.md) özelliğinin nasıl kullanılacağı gösterilmektedir.

 *Test-ilk geliştirme* , ürün belirtimlerine göre birim testlerini ilk kez yazacağınız ve sonra testlerin başarılı olması için gereken kaynak kodu yazdığınız yazılım tasarımına yönelik bir yaklaşımdır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], test durumlarınıza ilk kez başvurulduklarında kaynak kodunda yeni türler ve Üyeler üreterek öncelikle test geliştirme desteği destekler.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], iş akışınıza en az kesintiyle yeni türler ve Üyeler üretir. Türler, Yöntemler, özellikler, alanlar veya oluşturucular için kod içinde geçerli konumunuzu bırakmadan, saplamalar oluşturabilirsiniz. Tür oluşturma seçeneklerini belirtmek için bir iletişim kutusu açtığınızda, odak iletişim kutusu kapandığında geçerli açık dosyaya hemen döner.

 Kullanımdan Oluştur özelliği, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ile tümleştirilen test çerçeveleri ile birlikte kullanılabilir. Bu konuda, Microsoft birim testi çerçevesi gösterilmiştir.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Bir Windows sınıf kitaplığı projesi ve bir test projesi oluşturmak için

1. @No__t_0 veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ' de yeni bir Windows sınıf kitaplığı projesi oluşturun. Kullanmakta olduğunuz dile bağlı olarak, `GFUDemo_VB` veya `GFUDemo_CS` adlandırın.

2. **Çözüm Gezgini**, üstteki çözüm simgesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın. **Yeni proje** iletişim kutusunda, sol taraftaki **Proje türleri** bölmesinde **Test**' e tıklayın.

3. **Şablonlar** bölmesinde, **birim testi projesi** ' ne tıklayın ve varsayılan UnitTestProject1 adını kabul edin. Aşağıdaki çizimde, [!INCLUDE[csprcs](../includes/csprcs-md.md)] ' de göründüğünde iletişim kutusu gösterilmektedir. @No__t_0, iletişim kutusu benzer şekilde görünür.

     ![Yeni test projesi iletişim kutusu](../ide/media/newproject-test.png "NewProject_Test") Yeni proje iletişim kutusu

4. **Yeni proje** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

5. Sınıf projenizde, **Çözüm Gezgini**, **Başvurular** girişine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

6. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** ' i seçin ve ardından birim testi projenizi seçin.

7. **Tamam** ' a tıklayarak **başvuru Yöneticisi** iletişim kutusunu kapatın.

8. **Class1** dosyasında, var olan **using** deyimlerinin son öğesinden hemen sonra, test projesi için bir **using** deyimi ekleyin:

    * Visual Basic, `Using UnitTestProject1` ekleyin

    * İçinde C#, `using UnitTestProject1;` ekleyin

9. Çözümünüzü kaydedin. Artık testleri yazmaya başlamaya hazırsınız

### <a name="to-generate-a-new-class-from-a-unit-test"></a>Birim testten yeni bir sınıf oluşturmak için

1. Test projesi UnitTest1 adlı bir dosya içerir. Kod düzenleyicisinde açmak için **Çözüm Gezgini** bu dosyaya çift tıklayın. Test sınıfı ve test yöntemi üretildi.

2. Sınıf `UnitTest1` bildirimini bulun ve `AutomobileTest` olarak yeniden adlandırın. ' C#De, bir `UnitTest1()` Oluşturucu varsa, `AutomobileTest()` olarak yeniden adlandırın.

    > [!NOTE]
    > IntelliSense artık IntelliSense deyimin tamamlanması için iki alternatif sağlıyor: *tamamlama modu* ve *öneri modu*. Sınıfların ve üyelerin tanımlanmadan önce kullanıldığı durumlar için öneri modunu kullanın. Bir IntelliSense penceresi açıkken, tamamlama modu ve öneri modu arasında geçiş yapmak için CTRL + ALT + ara çubuğu tuşlarına basabilirsiniz. Daha fazla bilgi için bkz. [IntelliSense 'ı kullanma](../ide/using-intellisense.md) . Öneri modu, bir sonraki adımda `Automobile` yazarken yardımcı olur.

3. @No__t_0 yöntemini bulun ve `DefaultAutomobileIsInitializedCorrectly()` olarak yeniden adlandırın. Bu yöntemin içinde, Aşağıdaki çizimlerde gösterildiği gibi `Automobile` adlı bir sınıfın yeni bir örneğini oluşturun. Bir derleme zamanı hatası gösteren dalgalı alt çizgi görünür ve tür adı altında akıllı etiket görüntülenir. Akıllı etiketin tam konumu, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../includes/csprcs-md.md)] kullanıp kullanmayacağınızı bağlı olarak değişir.

     ![Visual Basic akıllı etiket altı çizili](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB") Visual Basic

     ![C&#35; 'de akıllı etiket altı çizili](../ide/media/genclass-underline.png "GenClass_Underline") VisualC#

4. @No__t_0 adlı hiçbir tür tanımlanmamış olduğunu bildiren bir hata iletisi görmek için fare işaretçisini akıllı etiketin üzerine getirin. Akıllı etikete tıklayın veya CTRL + tuşlarına basın. (CTRL + Period) Aşağıdaki çizimlerde gösterildiği gibi, kullanımdan oluştur kısayol menüsünü açmak için.

     ![Visual Basic 'de akıllı etiket bağlam menüsü](../ide/media/genclass-smartvb.png "GenClass_SmartVB") Visual Basic

     ![C&#35; 'de akıllı etiket bağlam menüsü](../ide/media/genclass-smartcs.png "GenClass_SmartCS") VisualC#

5. Artık iki seçeneğiniz vardır. Test projenizde yeni bir dosya oluşturmak ve `Automobile` adlı boş bir sınıf ile doldurmak için **' sınıf otomobil ' sınıfı oluştur** ' a tıklayabilirsiniz. Bu, geçerli projede varsayılan erişim değiştiricilerine sahip yeni bir dosyada yeni bir sınıf oluşturmanın hızlı bir yoludur. Yeni tür **Oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a de tıklayabilirsiniz. Bu, sınıfı varolan bir dosyaya yerleştirmeyi ve dosyayı başka bir projeye eklemeyi içeren seçenekler sağlar.

     Aşağıdaki çizimde gösterilen **yeni tür oluştur** iletişim kutusunu açmak için **yeni tür oluştur** ' a tıklayın. **Proje** listesinde, test projesi yerine dosyayı kaynak kodu projesine eklemek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] söylemek için **GFUDemo_VB** veya **GFUDemo_CS** ' a tıklayın.

     ![Yeni tür oluştur iletişim kutusu](../ide/media/genotherdialog.png "Genotheriletişim kutusu") Yeni tür oluştur iletişim kutusu

6. İletişim kutusunu kapatmak ve yeni dosyayı oluşturmak için **Tamam** ' ı tıklatın.

7. **Çözüm Gezgini**, yeni otomobil. VB veya automobile.cs dosyasının orada olduğunu doğrulamak Için, GFUDemo_VB veya GFUDemo_CS proje düğümünün altına bakın. Kod düzenleyicisinde, odak hala `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`. Testinizi en az kesintiye göre yazmaya devam edebilirsiniz.

### <a name="to-generate-a-property-stub"></a>Bir özellik saplaması oluşturmak için

1. Ürün belirtiminin `Automobile` sınıfının `Model` ve `TopSpeed` adında iki ortak özelliğe sahip olduğunu varsayalım. Bu özellikler varsayılan Oluşturucu tarafından `"Not specified"` ve `-1` varsayılan değerleriyle başlatılmalıdır. Aşağıdaki birim testi varsayılan oluşturucunun özellikleri doğru varsayılan değerlerine ayarladiğini doğrular.

     Aşağıdaki kod satırını `DefaultAutomobileIsInitializedCorrectly` ekleyin.

     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]

     Kod `Automobile` üzerinde iki tanımsız özelliğe başvurduğundan akıllı bir etiket görünür. @No__t_0 için akıllı etikete tıklayın ve sonra **özellik saplaması oluştur**' a tıklayın. @No__t_0 özelliği için de bir özellik saplaması oluşturun.

     @No__t_0 sınıfında, yeni özelliklerin türleri içerikten doğru şekilde algılanır.

     Aşağıdaki çizimde akıllı etiket kısayol menüsü gösterilmektedir.

     ![Visual Basic özellik bağlam menüsü oluştur](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB") Visual Basic

     ![C&#35; 'de özellik bağlam menüsü oluştur](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS") VisualC#

### <a name="to-locate-the-source-code"></a>Kaynak kodunu bulmak için

1. Yeni özelliklerin oluşturulduğunu doğrulayabilmeniz için Automobile.cs veya otomobil. vb kaynak kodu dosyasına gitmek üzere **Git** özelliğini kullanın.

     **Git** özelliği, bir metin dizesini bir tür adı veya bir adın parçası gibi hızlıca girmenizi sağlar ve sonuç listesindeki öğesine tıklayarak istediğiniz konuma gidebilirsiniz.

     Kod düzenleyicisine tıklayıp CTRL +, (CTRL + virgül) tuşlarına basarak **şuraya git** iletişim kutusunu açın. Metin kutusuna `automobile` yazın. Listeden **otomobil** ' ye tıklayın ve ardından **Tamam**' a tıklayın.

     Aşağıdaki çizimde, penceresine **Git** penceresi gösterilmiştir.

     ![İletişim kutusuna git](../ide/media/navigate-2.png "Navigate_2") Pencereye git

### <a name="to-generate-a-stub-for-a-new-constructor"></a>Yeni bir Oluşturucu için bir saplama oluşturmak için

1. Bu test yönteminde, `Model` ve `TopSpeed` özelliklerini, belirttiğiniz değerlere sahip olacak şekilde başlatacak bir Oluşturucu saplaması oluşturacaksınız. Daha sonra, testi tamamlamaya daha fazla kod ekleyeceksiniz. Aşağıdaki ek test yöntemini `AutomobileTest` sınıfınıza ekleyin.

     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]

2. Yeni sınıf oluşturucusunun altındaki akıllı etikete tıklayın ve sonra **Oluşturucu saplama oluştur**' a tıklayın. @No__t_0 sınıf dosyasında, yeni oluşturucunun Oluşturucu çağrısında kullanılan yerel değişkenlerin adlarını incelediğine, `Automobile` sınıfında aynı adlara sahip olan özelliklerin ve bu dosyayı depolamak için Oluşturucu gövdesinde sağlanmış olan kodun bulunduğunu unutmayın. `Model` ve `TopSpeed` özelliklerindeki bağımsız değişken değerleri. (@No__t_0, yeni oluşturucudaki `_model` ve `_topSpeed` alanları, `Model` ve `TopSpeed` özellikleri için örtük olarak tanımlanan yedekleme alanlarıdır.)

3. Yeni oluşturucuyu oluşturduktan sonra, `DefaultAutomobileIsInitializedCorrectly` varsayılan oluşturucuya yapılan çağrının altında dalgalı bir alt çizgi görünür. Hata mesajı, `Automobile` sınıfının sıfır bağımsız değişken alan bir Oluşturucusu olmadığını belirtir. Parametreleri olmayan açık bir varsayılan oluşturucu oluşturmak için akıllı etikete tıklayın ve sonra **Oluşturucu saplama oluştur**' a tıklayın.

### <a name="to-generate-a-stub-for-a-method"></a>Bir yöntem için saplama oluşturmak için

1. Belirtiminin, `Model` ve `TopSpeed` özellikleri varsayılan değerlerden başka bir değere ayarlandıysa, yeni bir `Automobile` çalışır duruma koyabileceğini belirtir. @No__t_0 yöntemine aşağıdaki satırları ekleyin.

     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]

2. @No__t_0 yöntemi çağrısının akıllı etiketine tıklayın ve ardından **Yöntem saplaması oluştur**' a tıklayın.

3. @No__t_0 özelliğinin akıllı etiketine tıklayın ve sonra **özellik saplaması oluştur**' a tıklayın. @No__t_0 sınıfı artık aşağıdaki kodu içerir.

     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]

### <a name="to-run-the-tests"></a>Testleri çalıştırmak için

1. **Birim testi** menüsünde, **birim testlerini Çalıştır**' ın üzerine gelin ve ardından **tüm sınamalar**' ı tıklatın. Bu komut, geçerli çözüm için yazılan tüm test çerçevelerinden tüm testleri çalıştırır.

     Bu durumda, iki test vardır ve beklendiği gibi her ikisi de başarısız olur. @No__t_1 koşulu `False` döndürdüğünden `DefaultAutomobileIsInitializedCorrectly` test başarısız olur. @No__t_2 sınıfındaki `Start` yöntemi bir özel durum oluşturduğundan `AutomobileWithModelNameCanStart` test başarısız olur.

     **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Başarısız olan test sonuçları](../ide/media/testsfailed.png "TestsFailed") Test Sonuçları penceresi

2. **Test sonuçları** penceresinde, her test hatasının konumuna gitmek için her test sonucu satırına çift tıklayın.

### <a name="to-implement-the-source-code"></a>Kaynak kodu uygulamak için

1. @No__t_0, `TopSpeed` ve `IsRunning` özelliklerinin `"Not specified"`, `-1` ve `True` doğru varsayılan değerlerine (`true`) başlatılması için aşağıdaki kodu varsayılan oluşturucuya ekleyin.

     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]

2. @No__t_0 yöntemi çağrıldığında, `IsRunning` bayrağını yalnızca, `Model` veya `TopSpeed` özellikleri varsayılan değerleri dışında bir değere ayarlandıysa true olarak ayarlanmalıdır. Yöntem gövdesinden `NotImplementedException` kaldırın ve aşağıdaki kodu ekleyin.

     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]

### <a name="to-run-the-tests-again"></a>Testleri yeniden çalıştırmak için

1. **Test** menüsünde, **Çalıştır**' ın üzerine gelin ve ardından **Çözümdeki tüm testler**' e tıklayın. Testlerin geçişi bu kez yapılır. **Test sonuçları** penceresi aşağıdaki çizimde gösterilmiştir.

     ![Geçilen test sonuçları](../ide/media/testspassed.png "Testsgeçti") Test Sonuçları penceresi

## <a name="see-also"></a>Ayrıca Bkz.
 [IntelliSense birimini kullanarak](../ide/using-intellisense.md) [kullanım](../misc/generate-from-usage.md) [yazma kodundan](../ide/writing-code-in-the-code-and-text-editor.md) oluşturma [kodunuzu test](../test/unit-test-your-code.md) etme
