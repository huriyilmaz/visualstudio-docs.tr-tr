---
title: İş Verileri Bağlantı Modeli | Microsoft Docs
description: İş verileri bağlantısı (BDC) modeli tasarlama. Varlıkları ve yöntemleri ekleyin. Yöntem parametrelerini tanımlayın. Filtre tanımlayıcıları ekleyin. BDC modelini doğrulama.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 831fe9dfe29744a395dc07a7c3d2d0ac901a43ab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628215"
---
# <a name="design-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli tasarlama
  Bir model dosyasına varlıklar ve yöntemler ekleyerek İş Verileri Bağlantısı (BDC) hizmeti için bir model geliştirebilirsiniz. Varlık, veri alanlarının koleksiyonunu açıklar. Örneğin, bir varlık veritabanındaki bir tabloyu temsil eder. Yöntem, varlıklar tarafından temsil edilen verileri ekleme, silme veya güncelleştirme gibi bir görev gerçekleştirir. Daha fazla bilgi için [bkz. İş verilerini SharePoint.](../sharepoint/integrating-business-data-into-sharepoint.md)

## <a name="add-entities"></a>Varlık ekleme
 Visual Studio Toolbox'tan BDC Designer'a bir Varlık sürükleyerek **veya kopyalayıp** varlık ekleme.  Daha fazla bilgi için [bkz. Nasıl kullanılır: Modele varlık ekleme.](../sharepoint/how-to-add-an-entity-to-a-model.md)

 Bir sınıfta varlığın alanlarını tanımlayın. Örneğin, bir sınıfa adlı bir `Address` alan `Customer` ekebilirsiniz. Projeye yeni bir sınıf ekleyebilir veya Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) gibi diğer araçları kullanarak oluşturulmuş mevcut bir sınıfı kullanabilirsiniz. Varlığın adı ve varlığı temsil eden sınıfın adının eşleşmesi gerek değildir. Modelinize yöntemleri tanımlarken sınıfı varlıkla ilişkilendirmeniz gerekir.

## <a name="add-methods"></a>Metot ekleme
 BDC hizmeti, kullanıcılar modelinizi temel alan bir liste veya Web Bölümü'ne bilgileri görüntüleye, ekleyene, güncelleştirene veya silen modelde yöntemleri arar. Kullanıcı tarafından gerçekleştirilen her görev için modele bir yöntem eklemeniz gerekir. BDC Yöntem Ayrıntıları penceresinden beş temel yöntem türünden birini **seçerek yöntemler** oluşturun. Aşağıdaki tabloda, bir BDC modelinin beş temel yöntemi açık almaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|Bulucu|Varlık örnekleri koleksiyonunu döndürür. Kullanıcı listeyi veya Web Bölümünü açtığında çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Finder method](../sharepoint/how-to-add-a-finder-method.md).|
|Belirli Bir Bulucu|Belirli bir varlık örneğini döndürür. Kullanıcı bir listede belirli bir öğenin ayrıntılarını görüntülerken çağrılır. Daha fazla bilgi için [bkz. Nasıl yapılacaklar: Belirli bir Finder yöntemi ekleme.](../sharepoint/how-to-add-a-specific-finder-method.md)|
|Oluşturucu|Varlığın veri kaynağına yeni veriler ekler. Kullanıcılar modeli temel **alan bir** listenin Şeridinde Yeni Öğe düğmesini seçtiklerine çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Creator method](../sharepoint/how-to-add-a-creator-method.md).|
|Güncelleştirici|Bir listede verileri değiştiren. Kullanıcılar bir listede bilgileri güncelleştirenler olduğunda çağrılır. Daha fazla bilgi için, [bkz. How to: Add an Updater method](../sharepoint/how-to-add-an-updater-method.md).|
|Silici|Verileri kaldırır. Kullanıcılar listeden bir öğe silebilirken çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Deleter method](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Yöntem parametrelerini tanımlama
 Bir yöntem oluştururken Visual Studio türüne uygun giriş ve çıkış parametrelerini ekler. Bu parametreler yalnızca yer tutucudur. Çoğu durumda, parametreleri değiştirerek doğru veri türünü geçmelerini veya geri dönmelerini sağlar. Örneğin, finder yöntemi varsayılan olarak bir dize döndürür. Çoğu durumda Finder yönteminin dönüş parametresini varlık koleksiyonu döndürerek değiştirmek istersiniz. Parametrenin tür tanımlayıcısını değiştirerek bunu gerçekleştirin. Tür tanımlayıcısı, bir parametrenin veri türünü açıklayan öznitelik koleksiyonudur. Daha fazla bilgi [için, bkz. How to: Define the type descriptor of a parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio, tür tanımlayıcılarını modelde parametreler arasında kopyalamaya olanak sağlar. Örneğin, yönteminin dönüş parametresi için `CustomerTD` adlı bir tür tanımlayıcısı `GetCustomer` tanımlayabilirsiniz. `CustomerTD`BDC Gezgini'nde tür tanımlayıcısını **kopyalayıp** bu tür tanımlayıcısını yönteminin giriş parametresine `CreateCustomer` yapıştırabilirsiniz. Bu, aynı tür tanımlayıcısını birden çok kez tanımlamak zorunda kalmamanizi sağlar.

## <a name="method-instances"></a>Yöntem örnekleri
 Bir yöntem oluştururken, Visual Studio bir varsayılan yöntem örneği ekler. Yöntem örneği, bir yöntemin başvurusu ve parametrelerin varsayılan değerleridir. Tek bir yöntemin birden çok yöntem örneği olabilir. Her örnek, yöntem imzası ile bir varsayılan değer kümesi birleşimidir. Daha fazla bilgi [için, bkz. How to: Define the type descriptor of a parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Projeyi çalıştırarak yöntem örnekleri, çalışma listesi üzerindeki açılan listede SharePoint görünür. Kullanıcılar verileri görüntülemek için yöntem örneklerini seçebilir.

 Yöntem örneğine varsayılan değerler eklemek için modelin XML'ini doğrudan değiştirmeniz gerekir. Daha fazla bilgi için bkz. [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Filtre tanımlayıcıları ekleme
 Modelin tüketicileri, bir varlığın bazı ölçütlere uyan örneklerini almak istiyor olabilir. Bu işlevi etkinleştirmek için bir yönteme filtre tanımlayıcısı ekleyebilirsiniz. Filtre tanımlayıcıları, model tüketicilerinin yürütmeden önce yöntemlere değer geçerek yöntem sonuç kümelerini filtrelemesini sağlar. Daha fazla bilgi için, [bkz. How to: Add Filter Parameters to Operations to Limit Instances from the External System](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint kullanıcıların filtre değerleri sağlamalarını sağlayan çeşitli özellikler sağlar. Örneğin, İş Verileri Web Bölümleri bir filtre metin kutusu sağlar. Kullanıcılar, metin kutusuna bir değer girerek bir listede yer alan verileri sınırlar. Bir yönteme filtre tanımlayıcısı ekleme hakkında daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Finder yöntemine filtre tanımlayıcısı ekleme.](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)

### <a name="filter-descriptor-properties"></a>Filtre tanımlayıcısı özellikleri
 Bir filtre tanımlayıcısının **İlişkili Tür Tanımlayıcısı,** **Ad** ve **Tür özelliklerinin** değerini ayarlayabilirsiniz. Diğer tüm özellikler isteğe bağlıdır.

 İlişkili **Tür Tanımlayıcısı özelliği,** filtre tanımlayıcısını bir giriş parametresiyle ilişkilendirildi. Kullanıcı bir filtre değeri sağladığında, BDC hizmeti giriş parametresini kullanarak bu değeri yöntemine iletir.

 **Type** özelliği, kullanmak istediğiniz filtreleme desenini açıklar. Bu SharePoint, seçerek filtre deseni, kullanıcı arabiriminde (UI) Kullanıcı Arabirimi etkiler. Örneğin, bir Karşılaştırıcı filtreleme düzeni için  metin, İş Verileri Web Bölümü üzerinde denetim olarak görünene eşittir. Her filtreleme deseni hakkında daha fazla bilgi için [bkz. BDC tarafından Desteklenen Filtre Türleri.](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))

 Bir filtre tanımlayıcısının özellikleri hakkında daha fazla bilgi için bkz. [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Varsayılan değerleri sağlama
 Bazı durumlarda kullanıcı bir filtre değeri sağlamay olabilir. Yöntem örneğine varsayılan değer ekleyerek veya yönteminizin kodunda varsayılan değeri ayarerek varsayılan bir değer sebilirsiniz. Yöntem örneğine varsayılan değer ekleme hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Yönteminizin kodunda bir giriş parametresinin varsayılan değerini ayarlama örneği için [bkz. Nasıl kullanılır: Finder yöntemine filtre tanımlayıcısı ekleme.](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)

## <a name="validate-the-model"></a>Modeli doğrulama
 Geliştirme sırasında modelinizi doğrularsiniz. Visual Studio modelinizin beklendiği gibivuzasını önleyen sorunları tanımlar. Bu sorunlar, hata Visual Studio **görüntülenir.**

 BDC Tasarımcısı kısayol menüsünü açarak ve ardından Doğrula'yı seçerek modeli **doğruabilirsiniz.** Model herhangi bir hata içeriyorsa Hata Listesinde **görünür.** İmleci, listedeki hataya çift tıklayarak, hata içeren koda hızlıca taşıyabilirsiniz. Alternatif olarak, listedeki hataların ileri veya geri ilerlemek için **F8** veya **SHIFT** + **F8** tuşlarını tekrar tekrar seçebilirsiniz.

 Doğrulama hataları, modelin kuralları bir şekilde ihlal edildiğinde meydana gelebilir. Örneğin, bir tür tanımlayıcısının **IsCollection** özelliği **true** olarak ayarlanmışsa, ancak alt tür tanımlayıcıları yoksa, bir doğrulama hatası görüntülenir. Visual Studio **Hata Listesi** görüntülenen bazı hataları anlamak için bir BDC modeli kurallarına başvurmanız gerekebilir. Bir BDC modelinin kuralları hakkında daha fazla bilgi için bkz. [BDCMetadata şeması](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Modeli içeren çözümde hata ayıklama
 Visual Studio kodda hata ayıklaması yaptığınız için kodunuzda hata ayıklayabilirsiniz. Kodunuzda hata ayıklamak için, kodunuzda herhangi bir yere kesme noktaları ayarlayın ve ardından hata ayıklayıcıyı başlatın. Visual Studio SharePoint sitesini açar. SharePoint ' de, iş verilerinizi kullanan bir liste veya Web bölümü oluşturun. Ardından, kodunuzda adım adım ilerme yapabilirsiniz. SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz. [SharePoint çözümlerinde sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Ayrıca, projeye eklediğiniz özel derlemelerdeki kodda hata ayıklaması yapabilirsiniz. Ancak, özel bir derlemedeki kodda hata ayıklamak için, derlemeyi çözüm paketine eklemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Projenize özel bir derleme ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: BIR BDC özelliğine özel derleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)ekleme.

### <a name="configure-bdc-security"></a>BDC güvenliğini yapılandırma
 çözümünüzde hata ayıklayabilmeniz için SharePoint güvenlik ayarlarınızı değiştirmeniz gerekebilir. bu ayarları değiştirmek için, SharePoint 2010 merkezi yönetim Web sitesindeki iş verileri bağlantı hizmeti uygulamasını açın. **Meta veri deposu Izinlerini ayarla** iletişim kutusunda, kullanıcı hesabınızı ekleyin ve sonra aşağıdaki seçeneklerden birini belirleyin:

|Görev|Seçenek|
|----------|------------|
|Modelleri BDC hizmetine dağıtmak için.|Düzenle|
|modelinizdeki dış içerik türlerini (varlıklar) kullanarak listeler ve Web Bölümleri oluşturmak için.|Istemcilerde seçilebilir|
|Varlık verilerini oluşturmak, okumak, güncelleştirmek ve silmek için.|Yürütme|

 Bu ayarlar hakkında daha fazla bilgi için bkz. [Iş verileri bağlantı hizmeti yönetimi](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Ayrıca, bireysel modeller veya dış içerik türleri için güvenlik izinleri de ayarlayabilirsiniz. Bir modelin güvenlik izinlerinin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [İVB model yönetimi](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Dış içerik türünün güvenlik izinlerinin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [dış içerik türü yönetimi](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> yerel SharePoint sunucunuzdaki bir çözümde hata ayıklamak için bu ayarları kullanın. üretim SharePoint sunucusu 'nda BDC ile ilgili güvenlik ayarlarını yapılandırma hakkında daha fazla bilgi için bkz. [iş verileri bağlantı hizmetleri güvenliğine genel bakış](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Bozuk olan modelleri geri çek
 hata ayıklayıcıyı ilk kez başlattığınızda Visual Studio modelin tamamını SharePoint dağıtır. bundan sonra her seferinde, SharePoint modeli, dağıtımlar arasında yaptığınız değişikliklerle Visual Studio güncelleştirir.

 Visual Studio modeli SharePoint tamamen geri çekmek istediğiniz durumlar olabilir. Örneğin, bir model bozuk hale gelebilir.  modelinizi SharePoint için yeniden dağıtmak için, modelin **artımlı güncelleştirme** özelliğini **False** olarak ayarlayın ve ardından hata ayıklayıcıyı başlatın. **Artımlı güncelleştirme** özelliği, **BDC Gezgini**'nde modeli temsil eden düğümü seçtiğinizde **Özellikler** penceresinde görünür. Varsayılan olarak, modelin adı **BdcModel1**' dir.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modeldeki varlıkların tanımlayıcı adlarını değiştirme
 Modeli dağıttıktan sonra bir tanımlayıcının adını değiştirirseniz bir dağıtım hatası alabilirsiniz. Modelin **artımlı güncelleştirme** özelliğini **false** olarak ayarlayarak bu hatayı çözebilirsiniz. Modeli el ile geri çekin ve sonra çözümü yeniden dağıtmanız gerekir. daha fazla bilgi için bkz. [SharePoint çözümlerinde sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md). İlk olarak modeli dağıtmadan önce **artımlı güncelleştirme** özelliğini **false** olarak ayarlayarak bu hatadan kaçınabilirsiniz.

## <a name="locate-documentation-for-bdc-model-elements"></a>IVB model öğeleri için belgeleri bulma
 Visual Studio her varlık, yöntem veya oluşturduğunuz diğer öğe için modele bir XML öğesi ekler. Öğe öznitelikleri **Özellikler** penceresinde özellikler olarak görünür. modeli tasarlarken Visual Studio oluşturduğu öğeler ve öznitelikler hakkında daha fazla bilgi için bkz. [bdcmetadata şeması](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)|BDC 'nin bir modelini görsel olarak tasarlamak için kullanabileceğiniz araçları açıklar.|
|[Nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)|Modele dış içerik türleri veya varlıkların nasıl ekleneceğini gösterir.|
|[Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)|Kullanıcıların bir listedeki veya Web parçasındaki varlıkların listesini görüntülemesini sağlayan bir yöntemi nasıl ekleyebileceğiniz gösterilmektedir.|
|[Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)|Kullanıcıların belirli bir varlığın ayrıntılarını görüntülemesine olanak sağlayan bir yöntemi nasıl ekleyebileceğiniz gösterilmektedir.|
|[Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)|Kullanıcıların bir veri kaynağına doğrudan bir listeden veya Web bölümünden kayıt eklemesini sağlayan bir yöntemi nasıl ekleneceğini gösterir.|
|[Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)|Kullanıcıların bir liste veya Web bölümünün Kullanıcı arabirimindeki (UI) seçeneklerini kullanarak bir veri kaynağından veri kaldırmasını sağlayan bir yöntemi nasıl ekleyebileceğiniz gösterilmektedir.|
|[Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)|Kullanıcıların bir veri kaynağındaki veri kayıtlarını doğrudan bir listeden veya Web bölümünden değiştirmesine olanak sağlayan bir yöntemi nasıl ekleyebileceğiniz gösterilmektedir.|
|[Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)|bir yönteme giriş ve dönüş parametreleri eklemek için Visual Studio yöntem ayrıntıları penceresini nasıl kullanacağınızı gösterir.|
|[Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Modeldeki parametre veri türlerini nasıl tanımlayacağınızı gösterir.|
|[Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)|BDC 'nin çalıştırdığı bir yöntemin örneğini oluşturmayı gösterir.|
|[Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Kullanıcıların bir bulucu yöntemi tarafından döndürülen örnek sayısını nasıl sınırlayamayacağını gösterir.|
|[Varlıklar Arasında İlişkilendirme Oluşturma](../sharepoint/creating-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkileri nasıl tanımlayabileceğinizi açıklar. iş verileri Web Bölümleri, dış listeler ve özel uygulamalar bu veri ilişkilerini bir kullanıcı arabiriminde (uı) görüntüleyebilir.|
|[Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkileri nasıl tanımlayacağınızı gösterir.|
|[izlenecek yol: iş verileri kullanarak SharePoint dış liste](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|SharePoint dış listesinde kişileri görüntüleyen bir model oluşturma ve test etme hakkında adım adım yönergeler sağlar.|
|[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)|IVB hizmeti için model oluşturma ve tasarlama hakkında genel bakış sağlar.|
