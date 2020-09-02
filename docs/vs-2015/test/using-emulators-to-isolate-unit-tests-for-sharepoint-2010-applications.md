---
title: SharePoint 2010 uygulamaları için birim testlerini yalıtmak üzere öykünücüleri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: b681164c-c87a-4bd7-be48-ed77e1578471
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cc3560c1cbcebea9f61465240cd4e2c7a0f811f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667463"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Sharepoint 2010 uygulamaları için birim testlerini yalıtmak üzere öykünücüler kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft. SharePoint. Öykünücüler paketi Microsoft SharePoint 2010 uygulamaları için yalıtılmış birim testleri oluşturmanıza yardımcı olan bir kitaplıklar kümesi sağlar. Öykünücüler, SharePoint API 'sinin en sık kullanılan nesnelerini ve yöntemlerini taklit eden hafif bellek içi nesneler oluşturmak için [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) yalıtım çerçevesinden [Dolgu](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) kullanır. Bir SharePoint yöntemi öykünmez veya bir öykünücüsünün varsayılan davranışını değiştirmek istediğinizde, istediğiniz sonuçları sağlamak için Fakes dolgu oluşturabilirsiniz.

 Mevcut test yöntemleri ve sınıfları, öykünücü bağlamında çalışmak üzere kolayca dönüştürülebilir. Bu özellik, Çift kullanım testleri oluşturmanıza olanak sağlar. Çift kullanımlı bir test, gerçek SharePoint API 'sine ve öykünücüleri kullanan yalıtılmış birim testlerine karşı tümleştirme testleri arasında geçiş yapabilir.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [Gereksinimler](#BKMK_Requirements)

 [Asıl Web Bölümü örneği](#BKMK_The_AppointmentsWebPart_example)

 [Varolan bir testi dönüştürme](#BKMK_Converting_an_existing_test)

- [Öykünücü paketini bir test projesine ekleme](#BKMK_Adding_the_Emulators_package_to_a_test_project)

- [Öykünme ile test yöntemi çalıştırma](#BKMK__Running_a_test_method_in_the_emulation_context)

  [Çift kullanım sınıfları ve yöntemleri oluşturma](#BKMK_Creating_dual_use_classes_and_methods)

  [Bir çift kullanım testi sınıfı oluşturmak için TestInitialize ve TestCleanup özniteliklerini kullanma](#BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class)

  [Öykünülmüş olmayan SharePoint yöntemlerini işleme](#BKMK_Handling_non_emulated_SharePoint_methods)

  [Sıfırdan öykünme testleri yazma ve bir Özet](#BKMK_Writing_emulation_tests_from_scratch__and_a_summary)

  [Örnek](#BKMK_Example)

  [Öykünülmüş SharePoint türleri](#BKMK_Emulated_SharePoint_types)

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Gereklilik

- Microsoft SharePoint 2010 (SharePoint 2010 Server veya SharePoint 2010 Foundation)

- Microsoft Visual Studio Enterprise

- Microsoft SharePoint öykünücüleri NuGet paketi

  Ayrıca, [Visual Studio 'da birim testi temel bilgileri](../test/unit-test-basics.md) ve bazı [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)konuları hakkında bilgi sahibi olmanız gerekir.

## <a name="the-appointmentswebpart-example"></a><a name="BKMK_The_AppointmentsWebPart_example"></a> Asıl Web Bölümü örneği
 Asıl Web Bölümü, randevularınızın SharePoint listesini görüntülemenize ve yönetmenize olanak sağlar.

 ![Randevular Web Bölümü](../test/media/ut-emulators-appointmentswebpart.png "UT_EMULATORS_AppointmentsWebPart")

 Bu örnekte Web bölümünün iki yöntemini test edeceğiz:

- `ScheduleAppointment`Yöntemi yöntemine geçirilen liste öğesi değerlerini doğrular ve belirtilen SharePoint Web üzerinde bir listede yeni bir giriş oluşturur.

- `GetAppointmentsForToday`Yöntemi, bugünün randevularının ayrıntılarını döndürür.

  [Bu konuda](#BKMK_In_this_topic)

## <a name="converting-an-existing-test"></a><a name="BKMK_Converting_an_existing_test"></a> Varolan bir testi dönüştürme
 Bir SharePoint bileşenindeki bir yöntemin tipik testinde test yöntemi, SharePoint Foundation 'da geçici bir site oluşturur ve SharePoint bileşenlerini test için gereken kodun gerektirdiği siteye ekler. Test yöntemi daha sonra bileşenin bir örneğini oluşturur ve oluşturur. Testin sonunda site bozulmuş.

 `ScheduleAppointment`Test altındaki kodumuz yöntemi muhtemelen bileşen için yazılan ilk yöntemlerden biridir:

```
// method under test
public bool ScheduleAppointment(SPWeb web, string listName, string name,
    string phone, string email, string age, DateTime date, out string errorMsg)
{
    errorMsg = string.Empty;
    var badFormat = this.checkInput(name, phone, email, age);
    if (badFormat)
    {
        errorMsg = "Bad Format";
        return false;
    }
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);
    if (exists)
    {
        errorMsg = "Item already exists";
        return false;
    }
    SPListItemCollection items = web.Lists[listName].Items;
    // create item and populate fields
    SPListItem item = items.Add();
    item["Name"] = name;
    item["Phone"] = phone;
    item["Email"] = email;
    item["Age"] = age;
    item["Date"] = date.ToString("D");
    item.Update();
    return true;
}

```

 Yöntemdeki işlevin ilk testi şöyle `ScheduleAppointment` görünebilir:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 Bu test yöntemi, `ScheduleAppointment` yöntemin listeye doğru bir şekilde yeni bir giriş eklediğinden emin olsa da, bu, kodunuzun belirli davranışının bir testine göre Web bölümünün bir tümleştirme testi olur. SharePoint ve SharePoint API 'ye yönelik dış bağımlılıklar, testteki kullanıcı kodundan farklı nedenlerle testin başarısız olmasına neden olabilir `ScheduleAppointment` . SharePoint sitesini oluşturma ve yok etme içindeki ek yük, kodlama işleminin düzenli bir parçası olarak testin çok yavaş çalışmasına neden olabilir. Her test yöntemi için sitenin kurulumunu ve yok edilmesini gerçekleştirmek yalnızca etkili geliştirici birim testleri oluşturma sorununa çözer.

 Microsoft SharePoint öykünücüleri, en yaygın SharePoint API 'Lerinin davranışını taklit eden bir nesne kümesi ve "Double" yöntemi sağlar. Öykünülmüş Yöntemler SharePoint API 'sinin, SharePoint 'in çalıştırmasını gerektirmeyen hafif uygulamalarıdır. SharePoint API 'sine yapılan çağrıları, SharePoint Öykünücülerine yönelik iki katına kaldırmak için Microsoft Fakes 'i kullanarak testlerinizi yalıtın ve istediğiniz kodu test ettiğinizden emin olun. Öykünülen SharePoint yöntemlerini çağırdığınızda, istenen davranışı oluşturmak için Fakes 'i doğrudan kullanabilirsiniz.

 [Bu konuda](#BKMK_In_this_topic)

### <a name="adding-the-emulators-package-to-a-test-project"></a><a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Öykünücü paketini bir test projesine ekleme
 SharePoint öykünücülerini bir test projesine eklemek için:

1. Çözüm Gezgini ' de test projesi seçin.

2. Kısayol menüsünde **NuGet Paketlerini Yönet...** öğesini seçin.

3. **Çevrimiçi** kategorisini arayın `Microsoft.SharePoint.Emulators` ve ardından **Install**' ı seçin.

   ![SharePoint öykünücüleri NuGet paketi](../test/media/ut-emulators-nuget.png "UT_EMULATORS_Nuget")

   [Bu konuda](#BKMK_In_this_topic)

### <a name="running-a-test-method-with-emulation"></a><a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Öykünme ile test yöntemi çalıştırma
 Paketi yüklemek, projelerinize gerekli kitaplıklara başvurular ekler. Mevcut bir test sınıfında öykünücüleri kullanmayı kolaylaştırmak için, ad alanlarını ve ' ı `Microsoft.SharePoint.Emulators` ekleyin `Microsoft.QualityTools.Testing.Emulators` .

 Test yöntemlerinizin öykünmesinin etkinleştirilmesi için, yöntem gövdesini `using` nesne oluşturan bir deyime sarın `SharePointEmulationScope` . Örneğin:

```csharp

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // create the emulation scope with a using statement
    using (new SharePointEmulationScope())
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}

```

 Test yöntemi yürütüldüğünde, öykünücü çalışma zamanı, bu yöntemlere yapılan çağrıları Microsoft.SharePoint.Fakes.dll ' de belirtilen temsilcilere dönüştürmek için Microsoft Fakes 'i çağırır. Microsoft.SharePoint.Emulators.dll, öykünülmüş yöntemler için temsilcileri uygular ve gerçek SharePoint davranışını yakından geliştirir. Test yöntemi veya test altındaki bileşen bir SharePoint yöntemini çağırdığında, bu durum öykünmeye neden olur.

 ![Öykünücü yürütme akışı](../test/media/ut-emulators-flowchart.png "UT_EMULATORS_FlowChart")

 [Bu konuda](#BKMK_In_this_topic)

## <a name="creating-dual-use-classes-and-methods"></a><a name="BKMK_Creating_dual_use_classes_and_methods"></a> Çift kullanım sınıfları ve yöntemleri oluşturma
 Gerçek SharePoint API ve öykünücü kullanan yalıtılmış birim testlerinde her iki Tümleştirme testi için kullanılabilecek yöntemler oluşturmak için, `SharePointEmulationScope(EmulationMode)` test yöntemi kodunuzu kaydırmak üzere aşırı yüklenmiş oluşturucuyu kullanın. Sabit listesinin iki değeri, `EmulationMode` kapsamın öykünücüleri () kullanıp kullanmadığını `EmulationMode.Enabled` veya KAPSAMıN SharePoint API () kullanıp kullanmadığını belirtir `EmulationMode.Passthrough` .

 Örneğin, bir önceki testi çift kullanım olacak şekilde nasıl değiştirebileceğiniz aşağıda verilmiştir:

```csharp

// class level field specifies emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled;

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // emulation scope determined by emulatorMode
    using( SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

 [Bu konuda](#BKMK_In_this_topic)

## <a name="using-testinitialize-and-testcleanup-attributes-to-create-a-dual-use-test-class"></a><a name="BKMK_Using_TestInitialize_and_TestCleanup_attributes_to_create_a_dual_use_test_class"></a> Bir çift kullanım testi sınıfı oluşturmak için TestInitialize ve TestCleanup özniteliklerini kullanma
 Kullanarak bir sınıftaki testlerin tamamını veya çoğunu çalıştırırsanız `SharePointEmulationScope` öykünme modunu ayarlamak için sınıf düzeyi tekniklerden yararlanabilirsiniz.

- Ve ile ilişkilendirilen test sınıfı yöntemleri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> kapsamı oluşturabilir ve yok edebilir.

- `EmulationMode`Sınıfının sınıf düzeyinde ayarlanması, ve arasındaki mod değişikliğini otomatikleştirmenize olanak sağlayabilir `EmulationMode.Enabled` `EmulationMode.Passthrough` .

  İle ilişkilendirilen bir sınıf yöntemi `[TestInitialize]` her test yönteminin başlangıcında çalıştırılır ve `[TestCleanup]` her test yönteminin sonunda çalıştırlarla öznitelikli bir yöntemi çalışır. Sınıf düzeyinde nesne için bir özel alan bildirebilir `SharePointEmulationScope` , bunu `TestInitialize` öznitelikli yöntemde başlatabilir ve sonra `TestCleanup` öznitelikli yöntemde nesnesini atabilirsiniz.

  Seçimini otomatik hale getirmek için seçtiğiniz herhangi bir yöntemi kullanabilirsiniz `EmulationMode` . Bir yöntem, önişlemci yönergelerini kullanarak bir sembolün varlığını denetetmenin bir yoludur. Örneğin, test yöntemlerini Öykünücüler kullanarak bir sınıfta çalıştırmak için `USE_EMULATION` test proje dosyasında ya da yapı komut satırında gibi bir simge tanımlayabilirsiniz. Sembol tanımlanmışsa, bir sınıf düzeyi `EmulationMode` sabiti bildirilmiştir ve olarak ayarlanır `Enabled` . Aksi takdirde, sabit olarak ayarlanır `Passthrough` .

  Aşağıda, öykünücü yönergelerini ve `TestInitialize` `TestCleanup` öykünme modunu ayarlamak için ve öznitelikli yöntemleri kullanmayı gösteren test sınıfının bir örneği verilmiştir.

```csharp
//namespace declarations
...

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        ...// More tests

    }
}

```

 [Bu konuda](#BKMK_In_this_topic)

## <a name="handling-non-emulated-sharepoint-methods"></a><a name="BKMK_Handling_non_emulated_SharePoint_methods"></a> Öykünülmüş olmayan SharePoint yöntemlerini işleme
 Tüm SharePoint türleri benzetilmez ve bazı öykünülmüş türlerde tüm yöntemler öykünmez. Test edilen kod, öykünmemiş bir SharePoint yöntemini çağırırsa, yöntem bir `NotSupportedException` özel durum oluşturur. Bir özel durum oluştuğunda, SharePoint yöntemi için Fakes dolgusu eklersiniz.

 **SharePoint Fakes 'i ayarlama**

 Microsoft Fakes shims 'i açıkça çağırmak için:

1. Öykünmemiş bir SharePoint sınıfını dolgu yapmak istiyorsanız, Microsoft. SharePoint. Fakes dosyasını düzenleyin ve sınıfı shimmed sınıfları listesine ekleyin. [Microsoft Fakes 'Te kod oluşturma, derleme ve adlandırma kurallarının](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md) [kod oluşturma ve parçalamayı yapılandırma](https://msdn.microsoft.com/library/hh708916.aspx#bkmk_configuring_code_generation_of_stubs) bölümüne bakın.

    ![Çözüm Gezgini Fakes klasörü](../test/media/ut-emulators-fakesfilefolder.png "UT_EMULATORS_FakesFileFolder")

2. Microsoft SharePoint öykünücüleri paketini yükledikten sonra ve Microsoft. SharePoint. Fakes dosyasını düzenlediyseniz, test projesini en az bir kez yeniden derleyin. Projeyi oluşturmak, disk üzerindeki proje kök klasörünüzde **Fakesassembly** klasörünü oluşturur ve doldurur.

    ![FakesAssembly klasörü](../test/media/ut-emulators-fakesassemblyfolder.png "UT_EMULATORS_FakesAssemblyFolder")

3. **Fakesassembly** klasöründe bulunan **Microsoft.SharePoint.14.0.0.0.Fakes.dll** derlemesine bir başvuru ekleyin.

4. Seçim İçin test sınıfına `Microsoft.QualityTools.Testing.Fakes` `Microsoft.SharePoint.Fakes` ve kullanmak istediğiniz tüm iç içe ad alanına bir ad alanı yönergesi ekleyin `Microsoft.SharePoint.Fakes` .

   **Bir SharePoint yöntemi için dolgu temsilcisini uygulama**

   Örnek projemizdeki yöntemi, `GetAppointmentsForToday` [SPList. GetItems (SPQuery)](https://msdn.microsoft.com/library/ms457534.aspx) SharePoint API yöntemini çağırır.

```csharp
// method under test
public string GetAppointmentsForToday(string listName, SPWeb web)
{
    SPList list = web.Lists[listName];
    DateTime today = DateTime.Now;
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};
    var result = new System.Text.StringBuilder();
    foreach (SPListItem item in list.GetItems(listQuery))
    {
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);
    }
    return result.ToString();
}

```

 `SPList.GetItems(SPQuery)`Aşırı yüklenmiş `GetItems` yöntemin sürümü benzetilmemiş. Bu nedenle, içinde için var olan bir testi yalnızca sarmalama `GetAppointmentsForToday` `SharePoint.Emulation.Scope` başarısız olur. Çalışan bir test oluşturmak için, `ShimSPList.GetItemsSPQuery` test etmek istediğiniz sonuçları döndüren Fakes temsilcisinin bir uygulamasını yazmanız gerekir.

 İşte, `GetAppointmentsForTodayReturnsOnlyTodaysAppointments` Fakes temsilcisini uygulayan, var olan bir test yönteminin bir değişikliği. Gerekli değişiklikler açıklamalarda çağrılır:

> [!IMPORTANT]
> Açıkça Fakes dolgu oluşturan test yöntemleri `ShimNotSupported` , test bağlamda çalıştırıldığında bir özel durum oluşturur `EmulationMode.Passthrough` . Bu sorundan kaçınmak için, değeri ayarlamak için bir değişken kullanın `EmulationMode` ve değeri test eden bir bildirimde Fakes kodunu sarın `if` .

```csharp
// class level field to set emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled

[TestMethod]
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
{

    // create the emulation scope with a using statement
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);
        // insert 2 items into list
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
            "raisa@outlook.com", "55", date.ToString("D") });
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

        // use Fakes shims only if emulation is enabled
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}

        // Act
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
        list.Delete();

        // Assert
        Assert.IsTrue(result.Contains(String.Format(
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
            "Age: 55, Date: {0}", date.ToString("D"))));
        Assert.IsFalse(result.Contains("Name: Francis Totten"));
    }
}

```

 Bu yöntemde, ilk olarak öykünmesinin etkinleştirildiğini test ediyoruz. Bu durumda, listemize yönelik bir Fakes dolgusu nesnesi oluşturur `SPList` ve ardından temsilcisine bir yöntem oluşturup atarız `GetItemsSPQuery` . Temsilci, `Bind` çağıran öğesine döndürülen öğesine doğru liste öğesini eklemek Için Fakes yöntemini kullanır `ShimSPListItemCollection` .

 [Bu konuda](#BKMK_In_this_topic)

## <a name="writing-emulation-tests-from-scratch-and-a-summary"></a><a name="BKMK_Writing_emulation_tests_from_scratch__and_a_summary"></a> Sıfırdan öykünme testleri yazma ve bir Özet
 Önceki bölümlerde açıklanan öykünme ve çift kullanım testleri oluşturma teknikleri, var olan testleri dönüştürdüğünü varsaysa da, testleri sıfırdan yazmak için de teknikleri kullanabilirsiniz. Aşağıdaki listede bu teknikler özetlenmektedir:

- Bir test projesinde öykünücüleri kullanmak için, projeye Microsoft. SharePoint. öykünücü NuGet paketini ekleyin.

- Bir test yönteminde öykünücüleri kullanmak için, `SharePointEmulationScope` yönteminin başlangıcında bir nesne oluşturun. Desteklenen tüm SharePoint API 'Leri, kapsam atılana kadar öykünülecektir.

- Test kodunuzu gerçek SharePoint API 'sine göre yazdıkça yazın. Öykünme bağlamı, SharePoint yöntemlerine yapılan çağrıların öykünücülerini otomatik olarak kaldırır.

- Tüm SharePoint nesneleri benzetilmez ve bazı öykünülmüş nesnelerin tüm yöntemleri öykünmez. `NotSupportedException`Öykünmemiş bir nesne veya yöntem kullandığınızda bir özel durum oluşturulur. Bu gerçekleştiğinde, gerekli davranışı döndürmek için yöntemi için açıkça bir Fakes dolgusu temsilcisi oluşturun.

- Çift kullanım testleri oluşturmak için, `SharePointEmulationScope(EmulationMode)` öykünme kapsamı nesnesini oluşturmak için oluşturucuyu kullanın. `EmulationMode`Değer, SharePoint çağrılarının gerçek bir SharePoint sitesine karşı öykündüğü veya yürütülüp yürütülmediğini belirtir.

- Test sınıfındaki test yöntemlerinizin tümü veya çoğu öykünme bağlamında yürütülebildiği takdirde, `TestInitialize` `SharePointEmulationScope` öykünme modunu ayarlamak için nesne ve sınıf düzeyi alanı oluşturmak için sınıf düzeyinde öznitelikli bir yöntemi kullanabilirsiniz. Bu, öykünme modunun değiştirilmesini otomatikleştirmenize yardımcı olur. Ardından `TestCleanup` , kapsam nesnesini atmak için Öznitelikli bir yöntemi kullanın.

  [Bu konuda](#BKMK_In_this_topic)

## <a name="example"></a><a name="BKMK_Example"></a> Örneğinde
 Yukarıda açıklanan SharePoint öykünücü tekniklerini içeren son bir örnek aşağıda verilmiştir:

```csharp
using System;
//other namespace declarations
...
// code under test
using MySPApps;
using Microsoft.SharePoint;
// unit testing and emulators
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.QualityTools.Testing.Emulators;
using Microsoft.SharePoint.Emulators;
// explicit Fakes shims
using Microsoft.QualityTools.Testing.Fakes;
using Microsoft.SharePoint.Fakes

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATION
            private const EmulationMode emulatorMode = EmulationMode.Enabled;
        #else
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;
        #endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]
        public void InitializeTest()
        {
            this.emulationScope = new SharePointEmulationScope(emulatorMode);
        }

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]
        public void Cleanup()
        {
            this.emulationScope.Dispose();
        }

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        [TestMethod]
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
        {

            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);
                // insert 2 items into list
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
                    "raisa@outlook.com", "55", date.ToString("D") });
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

                // use Fakes shims only if emulation is enabled
                if (emulatorMode == EmulationMode.Enabled)
                {
                    var sList = new ShimSPList(list);

                    sList.GetItemsSPQuery = (query) =>
                    {
                        var shim = new ShimSPListItemCollection();
                        shim.Bind(new[] { list.Items[0] });
                        return shim.Instance;
                    }
                }

                // Act
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
                list.Delete();

                // Assert
                Assert.IsTrue(result.Contains(String.Format(
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
                    "Age: 55, Date: {0}", date.ToString("D"))));
                Assert.IsFalse(result.Contains("Name: Francis Totten"));
            }
        }

        ...// More tests

    }
}

```

## <a name="emulated-sharepoint-types"></a><a name="BKMK_Emulated_SharePoint_types"></a> Öykünülmüş SharePoint türleri
 [Microsoft. SharePoint. SPField](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPField)

 [Microsoft. SharePoint. Spfieldındex](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndex)

 [Microsoft. SharePoint. Spfieldındexcollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldIndexCollection)

 [Microsoft. SharePoint. SPFieldLink](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLink)

 [Microsoft. SharePoint. SPFieldLinkCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldLinkCollection)

 [Microsoft. SharePoint. SPFieldUrlValue](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFieldUrlValue)

 [Microsoft. SharePoint. SPFile](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFile)

 [Microsoft. SharePoint. SPFileCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFileCollection)

 [Microsoft. SharePoint. SPFolder](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolder)

 [Microsoft. SharePoint. SPFolderCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPFolderCollection)

 [Microsoft. SharePoint. Spıtem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItem)

 [Microsoft. SharePoint. SPItemEventDataCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventDataCollection)

 [Microsoft. SharePoint. SPItemEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPItemEventProperties)

 [Microsoft. SharePoint. SPList](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPList)

 [Microsoft. SharePoint. SPListCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListCollection)

 [Microsoft. SharePoint. SPListEventProperties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListEventProperties)

 [Microsoft. SharePoint. SPListItem](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItem)

 [Microsoft. SharePoint. Spstitemcollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPListItemCollection)

 [Microsoft. SharePoint. SPQuery](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPQuery)

 [Microsoft. SharePoint. Sprotaatama](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignment)

 [Microsoft. SharePoint. Spromaatamamentcollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPRoleAssignmentCollection)

 [Microsoft. SharePoint. SPSecurableObject](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurableObject)

 [Microsoft. SharePoint. SPSecurity](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSecurity)

 [Microsoft. SharePoint. SPSite](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite)

 [Microsoft. SharePoint. SPUser](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUser)

 [Microsoft. SharePoint. SPUserCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPUserCollection)

 [Microsoft. SharePoint. SPView](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPView)

 [Microsoft. SharePoint. SPViewCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewCollection)

 [Microsoft. SharePoint. SPViewContext](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewContext)

 [Microsoft. SharePoint. SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb)

 [Microsoft. SharePoint. SPWebCollection](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWebCollection)

 [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod testi](../test/unit-test-your-code.md) , [kodlanmış UI testleri](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md) [Web performansı ve yük testi SharePoint 2010 2013 ve](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) SharePoint [çözümleri geliştiren](https://msdn.microsoft.com/library/059bce0f-c301-4234-a0b4-9c14b7cdfa3e) SharePoint 2010 uygulamalarını test edin.
