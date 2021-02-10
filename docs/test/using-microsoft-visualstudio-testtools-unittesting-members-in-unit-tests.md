---
title: Birim testlerinde MSTest kullanın
description: Visual Studio 'da birim testini destekleyen MSTest Framework hakkında bilgi edinin. Birim testlerini kodlarınızda bu sınıfları ve üyeleri kullanın.
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 4eef06bb48730fba9ba1df145857d41323cbfdd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946325"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Birim testlerinde MSTest çerçevesini kullanma

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) Framework, Visual Studio 'da birim testini destekler. <xref:Microsoft.VisualStudio.TestTools.UnitTesting>Birim testlerini kodlarunuzda, ad alanındaki sınıfları ve üyeleri kullanın. Ayrıca, koddan oluşturulmuş bir birim testini iyileştirirken de kullanabilirsiniz.

## <a name="framework-members"></a>Çerçeve üyeleri

Birim testi çerçevesine daha net bir genel bakış sağlamaya yardımcı olmak için, bu bölüm <xref:Microsoft.VisualStudio.TestTools.UnitTesting> ad alanının üyelerini ilgili işlevsellik grupları olarak düzenler.

> [!NOTE]
> Adları "Attribute" ile biten öznitelik öğeleri, sonunda ya da "Attribute" olmadan kullanılabilir. Örneğin, aşağıdaki iki kod örneği aynı şekilde çalışır:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Veri odaklı test için kullanılan Üyeler

Veri tabanlı birim testlerini ayarlamak için aşağıdaki öğeleri kullanın. Daha fazla bilgi için bkz. [veri temelli birim testi oluşturma](../test/how-to-create-a-data-driven-unit-test.md) ve bir [veri kaynağı tanımlamak Için yapılandırma dosyası kullanma](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Arama sırası oluşturmak için kullanılan öznitelikler

Aşağıdaki özniteliklerden biriyle donatılmış bir kod öğesi, belirttiğiniz anda çağırılır. Daha fazla bilgi için bkz. [birim testinin anatomi](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Derlemeler için öznitelikler

AssemblyInitialize ve AssemblyCleanup, derleme yüklenmeden hemen önce ve derleme bellekten kaldırıldıktan hemen sonra çağrılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Sınıfların öznitelikleri

Sınıfınız yüklenmeden ve sınıfınız bellekten kaldırılmadan önce ClassInitialize ve Classctaanup değeri hemen çağırılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Test yöntemleri için öznitelikler

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Test sınıflarını ve yöntemlerini tanımlamak için kullanılan öznitelikler

Her test sınıfının `TestClass` özniteliği olmalıdır ve her test yönteminin `TestMethod` özniteliği olmalıdır. Daha fazla bilgi için bkz. [birim testinin anatomi](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Onaylama sınıfları ve ilgili özel durumlar

Birim testleri, çeşitli onay, özel durum ve öznitelik türlerini kullanarak belirli uygulama davranışlarını doğrulayabilirler. Daha fazla bilgi için bkz. [onaylama sınıflarını kullanma](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>TestContext sınıfı

Aşağıdaki öznitelikler ve bunlara atanan değerler, belirli bir test yöntemi için Visual Studio Özellikler penceresi görüntülenir. Bu özniteliklere birim testinin kodu aracılığıyla erişilmek üzere tasarlanmamıştır. Bunun yerine, Visual Studio 'nun IDE 'si veya Visual Studio test altyapısı aracılığıyla, birim testinin kullanıldığı ya da çalıştırıldığı yolları etkiler. Örneğin, bu özniteliklerin bazıları **Test Yöneticisi** penceresinde ve **test sonuçları** penceresinde sütun olarak görünür, bu da testleri ve test sonuçlarını gruplamak ve sıralamak için bunları kullanabileceğiniz anlamına gelir. Bu tür bir özniteliği <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> , birim testlerine rastgele meta veriler eklemek için kullandığınız bir özniteliktir. Örneğin, birim testini ile işaretleyerek, bu testin kapsamakta olduğu bir test geçişinin adını depolamak için kullanabilirsiniz `[TestProperty("TestPass", "Accessibility")]` . Ya da bunu, sahip olduğu test türünün bir göstergesini depolamak için kullanabilirsiniz `[TestProperty("TestKind", "Localization")]` . Bu özniteliği kullanarak oluşturduğunuz özellik ve atadığınız Özellik değeri, her ikisi de başlık **testi** altındaki Visual Studio **özellikleri** penceresinde görüntülenir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Test yapılandırması sınıfları

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Rapor oluşturmak için kullanılan öznitelikler

Bu bölümdeki öznitelikler, bir Team Foundation Server takım projesinin proje hiyerarşisindeki varlıklarla süsledikleri test yöntemiyle ilgilidir.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Özel Erişimcilerde kullanılan sınıflar

Özel bir yöntem için birim testi oluşturabilirsiniz. Bu nesil, sınıfının bir nesnesini örnekleyen özel bir erişimci sınıfı oluşturur <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> . <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>Sınıfı, özel erişimci sürecinin bir parçası olarak yansıma kullanan bir sarmalayıcı sınıftır. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>Sınıf benzerdir, ancak özel örnek yöntemlerini çağırmak yerine özel statik yöntemleri çağırmak için kullanılır.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> başvuru belgeleri