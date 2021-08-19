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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060199"
---
# <a name="design-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli tasarlama
  Bir model dosyasına varlıklar ve yöntemler ekleyerek İş Verileri Bağlantısı (BDC) hizmeti için bir model geliştirebilirsiniz. Varlık, veri alanlarının bir koleksiyonunu açıklar. Örneğin, bir varlık veritabanındaki bir tabloyu temsil eder. Yöntem, varlıklar tarafından temsil edilen verileri ekleme, silme veya güncelleştirme gibi bir görevi gerçekleştirir. Daha fazla bilgi için [bkz. İş verilerini SharePoint.](../sharepoint/integrating-business-data-into-sharepoint.md)

## <a name="add-entities"></a>Varlık ekleme
 Visual Studio Toolbox'tan BDC Designer'a bir Varlık sürükleyerek **veya kopyalayıp** varlık ekleme.  Daha fazla bilgi için [bkz. Nasıl kullanılır: Modele varlık ekleme.](../sharepoint/how-to-add-an-entity-to-a-model.md)

 Bir sınıfta varlığın alanlarını tanımlayın. Örneğin, adlı bir alanı bir `Address` sınıfa `Customer` eklersiniz. Projeye yeni bir sınıf ekleyebilir veya Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) gibi diğer araçları kullanarak oluşturulmuş mevcut bir sınıfı kullanabilirsiniz. Varlığın adı ve varlığı temsil eden sınıfın adının eşleşmesi gerek değildir. Modelinize yöntemleri tanımlarken sınıfı varlıkla ilişkilendirmeniz gerekir.

## <a name="add-methods"></a>Metot ekleme
 BDC hizmeti, kullanıcılar modelinizi temel alan bir liste veya Web Bölümü'ne bilgileri görüntüleye, ekleyene, güncelleştirene veya silen modelde yöntemleri arar. Kullanıcı tarafından gerçekleştirilen her görev için modele bir yöntem eklemeniz gerekir. BDC Yöntem Ayrıntıları penceresinden beş temel yöntem türünden birini **seçerek yöntemler** oluşturun. Aşağıdaki tabloda, bir BDC modelinin beş temel yöntemi açık almaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|Bulucu|Varlık örnekleri koleksiyonunu döndürür. Kullanıcı listeyi veya Web Bölümünü açtığında çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Finder method](../sharepoint/how-to-add-a-finder-method.md).|
|Belirli Bir Bulucu|Belirli bir varlık örneğini döndürür. Kullanıcı bir listede belirli bir öğenin ayrıntılarını görüntülerken çağrılır. Daha fazla bilgi için, [bkz. How to: Add a specific Finder method](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Oluşturucu|Varlığın veri kaynağına yeni veriler ekler. Kullanıcılar modeli temel **alan bir** listenin Şeridinde Yeni Öğe düğmesini seçtiklerine çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Creator method](../sharepoint/how-to-add-a-creator-method.md).|
|Güncelleştirici|Bir listede verileri değiştiren. Kullanıcılar bir listede bilgileri güncelleştirenler olduğunda çağrılır. Daha fazla bilgi için, [bkz. How to: Add an Updater method](../sharepoint/how-to-add-an-updater-method.md).|
|Silici|Verileri kaldırır. Kullanıcılar listeden bir öğe silebilirken çağrılır. Daha fazla bilgi için, [bkz. How to: Add a Deleter method](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Yöntem parametrelerini tanımlama
 Bir yöntem oluştururken Visual Studio türüne uygun giriş ve çıkış parametrelerini ekler. Bu parametreler yalnızca yer tutucudur. Çoğu durumda, parametreleri değiştirerek doğru veri türünü geçmelerini veya geri dönmelerini sağlar. Örneğin, finder yöntemi varsayılan olarak bir dize döndürür. Çoğu durumda Finder yönteminin dönüş parametresini varlık koleksiyonu döndürerek değiştirmek istersiniz. Parametrenin tür tanımlayıcısını değiştirerek bunu gerçekleştirin. Tür tanımlayıcısı, bir parametrenin veri türünü açıklayan öznitelik koleksiyonudur. Daha fazla bilgi [için, bkz. How to: Define the type descriptor of a parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio, tür tanımlayıcılarını modelde parametreler arasında kopyalamaya olanak sağlar. Örneğin, yönteminin dönüş parametresi için `CustomerTD` adlı bir tür tanımlayıcısı `GetCustomer` tanımlayabilirsiniz. `CustomerTD`BDC Gezgini'nde tür tanımlayıcısını **kopyalayıp** bu tür tanımlayıcısını yönteminin giriş parametresine `CreateCustomer` yapıştırabilirsiniz. Bu, aynı tür tanımlayıcısını birden çok kez tanımlamak zorunda kalmamanizi sağlar.

## <a name="method-instances"></a>Yöntem örnekleri
 Bir yöntem oluştururken, Visual Studio bir yöntem örneği ekler. Yöntem örneği, bir yöntemin başvurusu ve parametrelerin varsayılan değerleridir. Tek bir yöntemin birden çok yöntem örneği olabilir. Her örnek, yöntem imzası ile bir varsayılan değer kümesi birleşimidir. Daha fazla bilgi [için, bkz. How to: Define the type descriptor of a parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Projeyi çalıştırarak yöntem örnekleri, çalışma listesi üzerindeki açılan listede SharePoint görünür. Kullanıcılar verileri görüntülemek için yöntem örneklerini seçebilir.

 Yöntem örneğine varsayılan değerler eklemek için modelin XML'ini doğrudan değiştirmeniz gerekir. Daha fazla bilgi için bkz. [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Filtre tanımlayıcıları ekleme
 Modelin tüketicileri, bir varlığın bazı ölçütlere uyan örneklerini almak istiyor olabilir. Bu işlevi etkinleştirmek için bir yönteme filtre tanımlayıcısı ekleyebilirsiniz. Filtre tanımlayıcıları, model tüketicilerinin yürütmeden önce yöntemlere değer geçerek yöntem sonuç kümelerini filtrelemesini sağlar. Daha fazla bilgi için, [bkz. How to: Add Filter Parameters to Operations to Limit Instances from the External System](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint kullanıcıların filtre değerleri sağlamalarını sağlayan çeşitli özellikler sağlar. Örneğin, İş Verileri Web Bölümleri bir filtre metin kutusu sağlar. Kullanıcılar, metin kutusuna bir değer girerek bir listede yer alan verileri sınırlar. Bir yönteme filtre tanımlayıcısı ekleme hakkında daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Finder yöntemine filtre tanımlayıcısı ekleme.](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)

### <a name="filter-descriptor-properties"></a>Filtre tanımlayıcısı özellikleri
 Bir filtre tanımlayıcısının **İlişkili Tür Tanımlayıcısı,** **Ad** ve **Tür özelliklerinin** değerini ayarlayabilirsiniz. Diğer tüm özellikler isteğe bağlıdır.

 İlişkili **Tür Tanımlayıcısı özelliği,** filtre tanımlayıcısını bir giriş parametresiyle ilişkilendirildi. Kullanıcı bir filtre değeri sağladığında, BDC hizmeti giriş parametresini kullanarak bu değeri yöntemine iletir.

 **Type** özelliği, kullanmak istediğiniz filtreleme desenini açıklar. Bu SharePoint, seçerek filtre deseni, kullanıcı arabiriminde (UI) Kullanıcı Arabirimi etkiler. Örneğin, Bir Karşılaştırıcı filtreleme düzeni için  metin, İş Verileri Web Bölümü üzerinde denetim olarak görünene eşittir. Her filtreleme deseni hakkında daha fazla bilgi için [bkz. BDC tarafından Desteklenen Filtre Türleri.](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))

 Bir filtre tanımlayıcısının özellikleri hakkında daha fazla bilgi için bkz. [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Varsayılan değerleri sağlama
 Bazı durumlarda kullanıcı bir filtre değeri sağlamay olabilir. Yöntem örneğine varsayılan değer ekleyerek veya yönteminizin kodunda varsayılan değeri ayarerek varsayılan bir değer sebilirsiniz. Yöntem örneğine varsayılan değer ekleme hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Yönteminizin kodunda bir giriş parametresinin varsayılan değerini ayarlama örneği için bkz. Nasıl [kullanılır: Finder yöntemine](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)filtre tanımlayıcısı ekleme.

## <a name="validate-the-model"></a>Modeli doğrulama
 Geliştirme sırasında modelinizi doğrularsiniz. Visual Studio modelinizin beklendiği gibivuzasını önleyen sorunları tanımlar. Bu sorunlar, hata Visual Studio **görüntülenir.**

 BDC Tasarımcısı'nın kısayol menüsünü açarak ve ardından Doğrula'yı seçerek modeli **doğruabilirsiniz.** Model herhangi bir hata içeriyorsa Hata Listesinde **görünür.** Listede hataya çift tıklayarak imleci hızla hata içeren koda doğru hareket ettirebilirsiniz. Alternatif olarak, listede hatalarda ileri veya geri gitmek için **F8** veya **Shift** + **F8** anahtarlarını tekrar tekrar seçebilirsiniz.

 Modelin kuralları bir şekilde ihlal edildiklerde doğrulama hataları oluşabilir. Örneğin, bir tür **tanımlayıcısının IsCollection** özelliği **true** olarak ayarlanırsa ancak alt tür tanımlayıcısı yoksa doğrulama hatası görüntülenir. hata listesinde görünen bazı hataları anlamak için bir BDC modelinin kurallarına Visual Studio **olabilir.** Bir BDC modelinin kuralları hakkında daha fazla bilgi için bkz. [BDCMetadata Şeması.](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))

## <a name="debug-the-solution-that-contains-the-model"></a>Modeli içeren çözümde hata ayıklama
 Kodda hata ayıklamak için kodda hata ayıklayabilirsiniz Visual Studio. Kodunuzun hatasını ayıklamak için kodunuzun herhangi bir yerinde kesme noktaları ayarlayın ve ardından hata ayıklayıcıyı başlatabilirsiniz. Visual Studio siteyi SharePoint açar. Bu SharePoint iş verilerinizi kullanan bir liste veya Web Bölümü oluşturun. Ardından, kodunuzun adım adımlarını atabilirsiniz. Projelerde hata ayıklama hakkında daha fazla SharePoint için [bkz. SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md)

 Ayrıca, projeye ekleyceğiniz özel derlemelerde kodda hata ayıkabilirsiniz. Ancak, özel bir derlemede kodda hata ayıklamak için derlemeyi çözüm paketine eklemeniz gerekir. Daha fazla bilgi için, [bkz. How to: Add and remove additional assemblies](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Projenize özel bir derleme ekleme hakkında daha fazla bilgi için [bkz.](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)Nasıl 2.

### <a name="configure-bdc-security"></a>BDC güvenliğini yapılandırma
 Çözümde hata ayıklamadan önce SharePoint ayarlarınızı değiştirmeniz gerekebilir. Bu ayarları değiştirmek için, SharePoint 2010 Merkezi Yönetim Web sitesinde İş Verileri Bağlantı Hizmeti Uygulamasını açın. Meta **Veri Deposu İzinlerini** Ayarla iletişim kutusunda kullanıcı hesabı ekleyin ve aşağıdaki seçeneklerden birini belirleyin:

|Görev|Seçenek|
|----------|------------|
|Modelleri BDC hizmetine dağıtmak için.|Düzenle|
|Modelde dış içerik Web Bölümleri (varlıklar) kullanarak listeler ve listeler oluşturmak için.|İstemcilerde Seçilebilir|
|Varlık verilerini oluşturmak, okumak, güncelleştirmek ve silmek için.|Yürütme|

 Bu ayarlar hakkında daha fazla bilgi için [bkz. İş Verileri Bağlantısı hizmet yönetimi.](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14))

 Ayrıca tek tek modeller veya dış içerik türleri için güvenlik izinleri de kullanabilirsiniz. Modelin güvenlik izinlerini ayarlama hakkında daha fazla bilgi için bkz. [BDC model yönetimi.](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)) Dış içerik türünün güvenlik izinlerini ayarlama hakkında daha fazla bilgi için bkz. [Dış içerik türü yönetimi.](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14))

> [!NOTE]
> Yerel sunucu sunucunuzda bir çözümde hata ayıklamak için SharePoint kullanın. Üretim sunucusu üzerinde BDC ile ilgili güvenlik ayarlarını yapılandırma hakkında daha fazla bilgi SharePoint bkz. [İş Verileri Bağlantı Hizmetleri güvenliğine genel bakış.](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14))

### <a name="retract-models-that-become-corrupt"></a>Bozuk olan modelleri geri alma
 Hata ayıklayıcıyı ilk kez başlatan Visual Studio modelin tamamını SharePoint. Bundan sonra her Visual Studio dağıtımlar arasında yaptığınız SharePoint değişikliklerle modeli güncelleştirmez.

 Modeli tamamen Visual Studio istediğiniz durumlar SharePoint olabilir. Örneğin, bir model bozulmuş olabilir.  Modelinizi yeni bir SharePoint için modelin **Artımlı Güncelleştirme** özelliğini **False** olarak ayarlayın ve ardından hata ayıklayıcıyı başlatabilirsiniz. **Artımlı** Güncelleştirme özelliği, BDC Gezgini'nde modeli temsil eden düğümü seçerek Özellikler **penceresinde görünür.**  Varsayılan olarak, modelin adı **BdcModel1'tir.**

### <a name="change-identifier-names-of-entities-in-the-model"></a>Modelde varlıkların tanımlayıcı adlarını değiştirme
 Modeli dağıtarak tanımlayıcının adını değiştirirsanız dağıtım hatası alabilirsiniz. Modelin Artımlı Güncelleştirme özelliğini False **olarak** ayarerek bu hatayı **çözesiniz.** Modeli el ile geri çekmeniz ve çözümü yeniden dağıtmanız gerekir. Daha fazla bilgi için [bkz. SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md) Modeli ilk dağıtmadan önce Artımlı **Güncelleştirme** özelliğini **False** olarak ayarerek bu hatayı ön alabilirsiniz.

## <a name="locate-documentation-for-bdc-model-elements"></a>BDC model öğelerinin belgelerini bulma
 Visual Studio her varlık, yöntem veya diğer öğe için modele bir XML öğesi ekler. Öğe öznitelikleri Özellikler penceresinde özellikler **olarak** görünür. Modeli tasarlarken oluşturulan öğeler ve Visual Studio hakkında bilgi için bkz. [BDCMetadata Şeması.](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)|BDC için görsel olarak bir model tasarlamak üzere kullanabileceğiniz araçları açıklar.|
|[Nasıl kullanılır: Modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)|Modele dış içerik türlerinin veya varlıkların nasıl ekli olduğunu gösterir.|
|[Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)|Kullanıcıların bir liste veya Web Bölümü'ne varlık listesini görüntülemesini sağlayan bir yöntemin nasıl ekli olduğunu gösterir.|
|[Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)|Kullanıcıların belirli bir varlığın ayrıntılarını görüntülemelerini sağlayan bir yöntemin nasıl ekli olduğunu gösterir.|
|[Nasıl yapılacaklar: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)|Kullanıcıların doğrudan bir listeden veya Web Bölümünden bir veri kaynağına kayıt eklemesini sağlayan bir yöntemin nasıl ekli olduğunu gösterir.|
|[Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)|Bir liste veya Web Bölümü'ne (UI) sahip seçenekler kullanarak kullanıcıların veri kaynağından veri kaldırmalarını Kullanıcı Arabirimi yöntemi nasıl ekleyebilirsiniz?|
|[Nasıl güncelleştirmesi: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)|Kullanıcıların bir veri kaynağında veri kayıtlarını doğrudan bir listeden veya Web Bölümünde değiştirmesini sağlayan bir yöntemin nasıl ekli olduğunu gösterir.|
|[Nasıl yapılanlar: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Yönteme giriş ve dönüş parametreleri eklemek için Visual Studio Ayrıntıları Penceresini nasıl kullanabileceğiniz gösterilir.|
|[Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Modelde parametre veri türlerini tanımlamayı gösterir.|
|[Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)|BDC'nin yürüttt olduğu bir yöntemin örneğini oluşturmanızı gösterir.|
|[Nasıl yapılacak: Bulıcı yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Kullanıcıların Bir Bulıcı yöntemi tarafından döndürülen örnek sayısını sınırlamalarını nasıl etkinleştirebilirsiniz?|
|[Varlıklar Arasında İlişkilendirme Oluşturma](../sharepoint/creating-an-association-between-entities.md)|Modelde varlıklar arasındaki ilişkileri nasıl tanımladığınız anlatmaktadır. İş Verileri Web Bölümleri, Dış Listeler ve özel uygulamalar bu veri ilişkilerini bir kullanıcı arabiriminde (UI) görüntüler.|
|[Nasıl kullanılır: Varlıklar arasında ilişki oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)|Modelde varlıklar arasındaki ilişkileri tanımlamayı gösterir.|
|[Adım adım kılavuz: İş verilerini kullanarak SharePoint dış liste oluşturma](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Bir dış listede kişileri görüntüleyen bir modelin nasıl oluşturul ve test SharePoint adım yönergeler sağlar.|
|[İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|BDC hizmeti için model oluşturma ve tasarlamaya genel bir bakış sağlar.|
