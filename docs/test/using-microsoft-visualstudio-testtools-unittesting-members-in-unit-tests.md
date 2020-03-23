---
title: Ünite testlerinde Microsoft.VisualStudio.TestTools.UnitTesting'i kullanma
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e45df63f36947b5f6f0aad77bb8eebcab4aca731
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585567"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Birim testlerinde MSTest çerçevesini kullanma

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) çerçevesi Visual Studio'da birim testini destekler. Birim testlerini kodlarken <xref:Microsoft.VisualStudio.TestTools.UnitTesting> ad alanındaki sınıfları ve üyeleri kullanın. Koddan oluşturulan bir birim testini rafine ederken bunları da kullanabilirsiniz.

## <a name="framework-members"></a>Çerçeve üyeleri

Birim sınama çerçevesinin daha net bir genel görünümünü sağlamaya <xref:Microsoft.VisualStudio.TestTools.UnitTesting> yardımcı olmak için, bu bölüm ad alanı nın üyelerini ilgili işlevsellik gruplarına ayırır.

> [!NOTE]
> Adları "Öznitelik" ile biten öznitelik öğeleri, sonunda "Öznitelik" ile veya "Öznitelik" olmadan kullanılabilir. Örneğin, aşağıdaki iki kod örneği aynı şekilde çalışır:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Veri tabanlı test için kullanılan üyeler

Veri tabanlı birim testleri ayarlamak için aşağıdaki öğeleri kullanın. Daha fazla bilgi için [bkz.](../test/how-to-create-a-data-driven-unit-test.md) [Use a configuration file to define a data source](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Arama emri oluşturmak için kullanılan öznitelikler

Belirttiğiniz anda, aşağıdaki özniteliklerden biriyle dekore edilmiş bir kod öğesi çağrılır. Daha fazla bilgi [için, bir birim testinin Anatomisi](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)bölümüne bakın.

### <a name="attributes-for-assemblies"></a>Derlemeler için öznitelikler

AssemblyInitialize ve AssemblyCleanup, derlemeniz yüklendikten hemen sonra ve derlemeniz boşaltılmadan hemen önce çağrılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Sınıflar için öznitelikler

ClassInitialize ve ClassCleanup, sınıfınız yüklendikten hemen sonra ve sınıf Kaldırılmadan hemen önce çağrılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Test yöntemleri için öznitelikler

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Test sınıflarını ve yöntemlerini tanımlamak için kullanılan öznitelikler

Her test sınıfı `TestClass` özniteliğe sahip olmalıdır ve `TestMethod` her test yöntemi özniteliğe sahip olmalıdır. Daha fazla bilgi [için, bir birim testinin Anatomisi](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)bölümüne bakın.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Sınıfları ve ilgili özel durumları öne sür

Birim testleri, belirli uygulama davranışını çeşitli türde iddialar, özel durumlar ve öznitelikleri kullanarak doğrulayabilir. Daha fazla bilgi için [bkz.](../test/using-the-assert-classes.md)

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>TestContext sınıfı

Belirli bir test yöntemi için Visual Studio Properties penceresinde aşağıdaki öznitelikler ve bunlara atanan değerler görünür. Bu özniteliklere birim testinin kodu yla erişilmesi amaçlanmaz. Bunun yerine, birim testinin kullanılma veya çalışma yöntemlerini, Visual Studio'nun IDE'si veya Visual Studio test motoru aracılığıyla etkiler. Örneğin, bu özniteliklerden bazıları **Test Yöneticisi** penceresinde ve **Test Sonuçları** penceresinde sütun olarak görünür, bu da bunları testleri gruplandırmak ve sıralamak ve sonuçları test etmek için kullanabileceğiniz anlamına gelir. Bu tür öznitelik, birim testleri için rasgele meta veri eklemek için kullandığınız. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> Örneğin, birim testini . ile işaretleyerek, bu testin kapsadığı bir `[TestProperty("TestPass", "Accessibility")]`test geçişinin adını depolamak için kullanabilirsiniz. Veya, test türünün bir göstergesini depolamak için `[TestProperty("TestKind", "Localization")]`kullanabilirsiniz. Bu özniteliği kullanarak oluşturduğunuz özellik ve atadığınız özellik değeri, **Test'e özgü**' başlığı altında Visual Studio **Properties** penceresinde görüntülenir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Yapılandırma sınıflarını test edin

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Rapor oluşturmak için kullanılan öznitelikler

Bu bölümdeki öznitelikler, takım foundation server takım projesinin proje hiyerarşisindeki varlıklarla dekore ettikleri test yöntemini ilişkilendirmektedir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Özel erişimcilerle kullanılan sınıflar

Özel bir yöntem için birim testi oluşturabilirsiniz. Bu nesil, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> sınıfın bir nesnesini anında alan özel bir erişimci sınıf oluşturur. Sınıf, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> yansımayı özel erişimci işleminin bir parçası olarak kullanan bir sarmalayıcı sınıfıdır. Sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> benzer, ancak özel örnek yöntemleri çağırmak yerine özel statik yöntemleri aramak için kullanılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>referans belgeleri
