---
title: Iş verileri bağlantı modeli tasarlama | Microsoft Docs
description: Bir iş verileri bağlantısı (BDC) modeli tasarlayın. Varlıklar ve yöntemler ekleyin. Yöntem parametrelerini tanımlayın. Filtre tanımlayıcıları ekleyin. IVB modelini doğrulayın.
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
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948849"
---
# <a name="design-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli tasarlama
  Bir model dosyasına varlıklar ve yöntemler ekleyerek Iş verileri bağlantısı (BDC) hizmeti için bir model geliştirebilirsiniz. Bir varlık, veri alanları koleksiyonunu açıklar. Örneğin, bir varlık veritabanındaki bir tabloyu temsil edebilir. Bir yöntem, varlıklar tarafından temsil edilen verileri ekleme, silme veya güncelleştirme gibi bir görevi gerçekleştirir. Daha fazla bilgi için bkz. [iş verilerini SharePoint Ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Varlık ekleme
 Bir varlığı, Visual Studio **araç kutusu** **'ndan BDC** Tasarımcısı üzerine sürükleyerek veya kopyalayarak bir varlık ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Bir sınıftaki varlık alanlarını tanımlayın. Örneğin, bir sınıfa adlı bir alan ekleyebilirsiniz `Address` `Customer` . Projeye yeni bir sınıf ekleyebilir veya Nesne İlişkisel Tasarımcısı (O/R Designer) gibi diğer araçları kullanarak oluşturulan mevcut bir sınıfı kullanabilirsiniz. Varlığın adı ve varlığı temsil eden sınıfın adı eşleşmelidir. Modelinizdeki yöntemleri tanımlarken, sınıfı varlıkla ilişkilendirebilirsiniz.

## <a name="add-methods"></a>Yöntem Ekle
 Kullanıcılar, modelinize bağlı bir liste veya Web Bölümü içindeki bilgileri görüntülerken, eklerken, Güncelleştir, Güncelleştir, Güncelleştir, güncelleyebilir veya silbir şekilde modelinizdeki yöntemleri çağırır. Kullanıcının gerçekleştirebileceği her görev için modele bir yöntem eklemeniz gerekir. **IVB yöntemi ayrıntıları** penceresinden beş temel yöntem türünden birini seçerek Yöntemler oluşturun. Aşağıdaki tabloda bir BDC modelinin beş temel yöntemi açıklanmaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|'Daki|Varlık örneklerinin bir koleksiyonunu döndürür. Kullanıcı listeyi veya Web bölümünü açtığında çağırılır. Daha fazla bilgi için bkz. [nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md).|
|Belirli Bir Bulucu|Belirli bir varlık örneğini döndürür. Bir Kullanıcı bir listedeki belirli bir öğenin ayrıntılarını görüntülediğinde çağırılır. Daha fazla bilgi için bkz. [nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Oluşturucu|Bir varlığın veri kaynağına yeni veri ekler. Kullanıcılar, modeli temel alan bir listenin şeridinde **Yeni öğe** düğmesini seçerken çağırılır. Daha fazla bilgi için bkz. [nasıl yapılır: Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md).|
|Güncelleştirici|Bir listedeki verileri değiştirir. Kullanıcılar bir listedeki bilgileri güncelleştirgeldiğinde çağırılır. Daha fazla bilgi için bkz. [nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md).|
|Silici|Verileri kaldırır. Kullanıcılar listeden bir öğeyi sileklerken çağırılır. Daha fazla bilgi için bkz. [nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Yöntem parametrelerini tanımlayın
 Bir yöntem oluşturduğunuzda, Visual Studio Yöntem türü için uygun olan giriş ve çıkış parametrelerini ekler. Bu parametreler yalnızca yer tutuculardır. Çoğu durumda, parametreleri doğru veri türünü geçecek veya döndürecek şekilde değiştirmeniz gerekir. Örneğin, varsayılan olarak, bir bulucu yöntemi bir dize döndürür. Çoğu durumda, Finder yönteminin dönüş parametresini bir varlık koleksiyonu döndürecek şekilde değiştirmek istersiniz. Parametrenin tür tanımlayıcısını değiştirerek bunu yapabilirsiniz. Tür tanımlayıcısı, bir parametrenin veri türünü açıklayan özniteliklerin koleksiyonudur. Daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio, modeldeki parametreler arasında tür tanımlayıcılarını kopyalamanızı sağlar. Örneğin, `CustomerTD` yönteminin Return parametresi için adlı bir tür tanımlayıcısı tanımlayabilirsiniz `GetCustomer` . `CustomerTD`Tür tanımlayıcısını **BDC Gezgini**' nde kopyalayabilir ve sonra bu tür tanımlayıcısını metodun giriş parametresine yapıştırabilirsiniz `CreateCustomer` . Bu, aynı tür tanımlayıcısını birden çok kez tanımlamanızı önler.

## <a name="method-instances"></a>Yöntem örnekleri
 Bir yöntem oluşturduğunuzda, Visual Studio varsayılan bir yöntem örneği ekler. Yöntem örneği bir yönteme başvurudur ve parametreler için varsayılan değerleri. Tek bir yöntem birden çok yöntem örneğine sahip olabilir. Her örnek, yöntem imzasının ve bir dizi varsayılan değerin birleşimidir. Daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Projeyi çalıştırdığınızda, yöntem örnekleri SharePoint listesinin üzerindeki bir açılan listede görüntülenir. Kullanıcılar, verileri görüntülemek için yöntem örnekleri seçebilirler.

 Yöntem örneğine varsayılan değerler eklemek için, modelin XML 'sini doğrudan değiştirmeniz gerekir. Daha fazla bilgi için bkz. [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Filtre tanımlayıcıları Ekle
 Modelin tüketicileri, bazı ölçütlerle eşleşen bir varlığın örneklerini almak isteyebilir. Bu işlevi etkinleştirmek için bir yönteme filtre tanımlayıcısı ekleyebilirsiniz. Filtre tanımlayıcıları, model tüketicilerinin yürütmeden önce yöntemlere değer geçirerek Yöntem sonuç kümelerini filtrelemesine olanak tanır. Daha fazla bilgi için bkz. [nasıl yapılır: olayları dış sistemden sınırlamak Için Işlemlere filtre parametreleri ekleme](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint, kullanıcıların filtre değerleri sağlamasını sağlayan çeşitli özellikler sağlar. Örneğin, Iş verileri Web Bölümleri bir filtre metin kutusu sağlar. Kullanıcılar bir listedeki verileri metin kutusuna bir değer girerek sınırlayabilir. Bir yönteme filtre tanımlayıcısı ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Filtre tanımlayıcısı özellikleri
 Bir filtre tanımlayıcısının **Ilişkili tür tanımlayıcısının**, **adının** ve **tür** özelliklerinin değerini ayarlamanız gerekir. Diğer tüm özellikler isteğe bağlıdır.

 **Ilişkili tür tanımlayıcısı** özelliği, filtre tanımlayıcısını bir giriş parametresiyle ilişkilendirir. Bir Kullanıcı bir filtre değeri sağlıyorsa, IVB hizmeti bu değeri giriş parametresini kullanarak yöntemine geçirir.

 **Type** özelliği, kullanmak istediğiniz filtreleme modelini açıklar. SharePoint 'te, seçtiğiniz filtreleme deseninin Kullanıcı arabiriminde (UI) görüntülenen metni etkiler. Örneğin, bir karşılaştırıcı filtreleme deseniyle **ilgili metin,** bir Iş verileri Web bölümünün üzerinde bir denetim olarak görünür. Her filtreleme deseninin hakkında daha fazla bilgi için bkz. [BDC tarafından desteklenen filtre türleri](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Bir filtre tanımlayıcısının özellikleri hakkında daha fazla bilgi için bkz. [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Varsayılan değerleri sağla
 Bazı durumlarda, Kullanıcı bir filtre değeri sağlayamayabilir. Yöntem örneğine varsayılan bir değer ekleyerek veya yönteminizin kodundaki varsayılan değeri ayarlayarak varsayılan bir değer sağlayabilirsiniz. Yöntem örneğine bir varsayılan değer ekleme hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Yönteminizin kodundaki bir giriş parametresinin varsayılan değerini ayarlamaya ilişkin bir örnek için bkz. [nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Modeli doğrulama
 Geliştirme sırasında modelinizi doğrulayabilirsiniz. Visual Studio, modelinizin beklendiği gibi davranmasını engelleyebilecek sorunları tanımlar. Bu sorunlar, Visual Studio **hata listesi** görüntülenir.

 Bir modeli, IVB Tasarımcısı için kısayol menüsünü açıp **Doğrula**' yı seçerek doğrulayabilirsiniz. Model herhangi bir hata içeriyorsa **hata listesi** görünürler. İmleci, listedeki hataya çift tıklayarak, hata içeren koda hızlıca taşıyabilirsiniz. Alternatif olarak, listedeki hataların ileri veya geri ilerlemek için **F8** veya **SHIFT** + **F8** tuşlarını tekrar tekrar seçebilirsiniz.

 Doğrulama hataları, modelin kuralları bir şekilde ihlal edildiğinde meydana gelebilir. Örneğin, bir tür tanımlayıcısının **IsCollection** özelliği **true** olarak ayarlanmışsa, ancak alt tür tanımlayıcıları yoksa, bir doğrulama hatası görüntülenir. Visual Studio **hata listesi** görünen bazı hataları anlamak IÇIN bir BDC modeli kurallarına başvurmanız gerekebilir. Bir BDC modelinin kuralları hakkında daha fazla bilgi için bkz. [BDCMetadata şeması](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Modeli içeren çözümde hata ayıklama
 Visual Studio 'da herhangi bir kodda hata ayıklaması yaptığınız için kodunuzda hata ayıklayabilirsiniz. Kodunuzda hata ayıklamak için, kodunuzda herhangi bir yere kesme noktaları ayarlayın ve ardından hata ayıklayıcıyı başlatın. Visual Studio, SharePoint sitesini açar. SharePoint 'te, iş verilerinizi kullanan bir liste veya Web bölümü oluşturun. Ardından, kodunuzda adım adım ilerme yapabilirsiniz. SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Ayrıca, projeye eklediğiniz özel derlemelerdeki kodda hata ayıklaması yapabilirsiniz. Ancak, özel bir derlemedeki kodda hata ayıklamak için, derlemeyi çözüm paketine eklemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: ek derlemeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Projenize özel bir derleme ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: BIR BDC özelliğine özel derleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)ekleme.

### <a name="configure-bdc-security"></a>BDC güvenliğini yapılandırma
 Çözümünüzde Hata ayıklayabilmeniz için SharePoint 'teki güvenlik ayarlarınızı değiştirmeniz gerekebilir. Bu ayarları değiştirmek için, SharePoint 2010 Merkezi Yönetim Web sitesindeki Iş verileri bağlantı hizmeti uygulamasını açın. **Meta veri deposu Izinlerini ayarla** iletişim kutusunda, kullanıcı hesabınızı ekleyin ve sonra aşağıdaki seçeneklerden birini belirleyin:

|Görev|Seçenek|
|----------|------------|
|Modelleri BDC hizmetine dağıtmak için.|Düzenle|
|Modelinizdeki dış içerik türlerini (varlıklar) kullanarak listeler ve Web Bölümleri oluşturmak için.|Istemcilerde seçilebilir|
|Varlık verilerini oluşturmak, okumak, güncelleştirmek ve silmek için.|Yürütme|

 Bu ayarlar hakkında daha fazla bilgi için bkz. [Iş verileri bağlantı hizmeti yönetimi](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Ayrıca, bireysel modeller veya dış içerik türleri için güvenlik izinleri de ayarlayabilirsiniz. Bir modelin güvenlik izinlerinin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [İVB model yönetimi](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Dış içerik türünün güvenlik izinlerinin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [dış içerik türü yönetimi](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Yerel SharePoint sunucunuzdaki bir çözümde hata ayıklamak için bu ayarları kullanın. Üretim SharePoint Server 'da BDC ile ilgili güvenlik ayarlarını yapılandırma hakkında daha fazla bilgi için bkz. [Iş verileri bağlantı Hizmetleri güvenliğine genel bakış](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Bozuk olan modelleri geri çek
 Hata ayıklayıcıyı ilk kez başlattığınızda, Visual Studio modelin tamamını SharePoint 'e dağıtır. Bundan sonra Visual Studio, SharePoint 'teki modeli dağıtımlar arasında yaptığınız değişikliklerle güncelleştirir.

 Visual Studio 'Nun modeli SharePoint 'ten tamamen geri çekmek istediğiniz durumlar olabilir. Örneğin, bir model bozuk hale gelebilir.  Modelinizi SharePoint 'e yeniden dağıtmak için, modelin **artımlı güncelleştirme** özelliğini **false** olarak ayarlayın ve ardından hata ayıklayıcıyı başlatın. **Artımlı güncelleştirme** özelliği, **BDC Gezgini**'nde modeli temsil eden düğümü seçtiğinizde **Özellikler** penceresinde görünür. Varsayılan olarak, modelin adı **BdcModel1**' dir.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modeldeki varlıkların tanımlayıcı adlarını değiştirme
 Modeli dağıttıktan sonra bir tanımlayıcının adını değiştirirseniz bir dağıtım hatası alabilirsiniz. Modelin **artımlı güncelleştirme** özelliğini **false** olarak ayarlayarak bu hatayı çözebilirsiniz. Modeli el ile geri çekin ve sonra çözümü yeniden dağıtmanız gerekir. Daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md). İlk olarak modeli dağıtmadan önce **artımlı güncelleştirme** özelliğini **false** olarak ayarlayarak bu hatadan kaçınabilirsiniz.

## <a name="locate-documentation-for-bdc-model-elements"></a>IVB model öğeleri için belgeleri bulma
 Visual Studio, her varlık, yöntem veya oluşturduğunuz diğer öğe için modele bir XML öğesi ekler. Öğe öznitelikleri **Özellikler** penceresinde özellikler olarak görünür. Modeli tasarlarken Visual Studio 'Nun oluşturduğu öğeler ve öznitelikler hakkında daha fazla bilgi için bkz. [BDCMetadata şeması](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

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
|[Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Bir yönteme giriş ve dönüş parametreleri eklemek için Visual Studio 'daki Yöntem ayrıntıları penceresini nasıl kullanacağınızı gösterir.|
|[Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Modeldeki parametre veri türlerini nasıl tanımlayacağınızı gösterir.|
|[Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)|BDC 'nin çalıştırdığı bir yöntemin örneğini oluşturmayı gösterir.|
|[Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Kullanıcıların bir bulucu yöntemi tarafından döndürülen örnek sayısını nasıl sınırlayamayacağını gösterir.|
|[Varlıklar Arasında İlişkilendirme Oluşturma](../sharepoint/creating-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkileri nasıl tanımlayabileceğinizi açıklar. İş verileri Web Bölümleri, dış listeler ve özel uygulamalar bu veri ilişkilerini bir kullanıcı arabiriminde (UI) görüntüleyebilir.|
|[Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkileri nasıl tanımlayacağınızı gösterir.|
|[İzlenecek yol: iş verileri kullanarak SharePoint 'te dış liste](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|SharePoint dış listesinde kişileri görüntüleyen bir model oluşturma ve test etme hakkında adım adım yönergeler sağlar.|
|[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)|IVB hizmeti için model oluşturma ve tasarlama hakkında genel bakış sağlar.|
