---
title: Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c366ce44ab65ded62370dd3c219473089d5ca111
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299570"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, dağıtılmış uygulamalar oluşturmaya yönelik Windows Communication Foundation (WCF) ve [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], Microsoft teknolojileri ile çalışmaya yönelik araçlar sağlar. Bu konu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] perspektifinden hizmetlere giriş sağlar. Tüm belgeler için bkz. [WCF Veri Hizmetleri 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>WCF nedir?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], güvenli, güvenilir, işlem temelli ve birlikte çalışabilen dağıtılmış uygulamalar oluşturmaya yönelik Birleşik bir çerçevedir. ASMX Web Hizmetleri, .NET uzaktan iletişim, Enterprise Hizmetleri (DCOM) ve MSMQ gibi eski işlemler arası iletişimi teknolojilerini değiştirir. WCF bu teknolojilerden birleşik bir programlama modeli altında işlevselliğini bir araya getirir. Bu, dağıtılmış uygulamalar geliştirme deneyimi basitleştirir.

#### <a name="what-are-wcf-data-services"></a>WCF Veri Hizmetleri nelerdir
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], açık veri (OData) protokolü standardının bir uygulamasıdır.  Tablolu verileri gibi standart HTTP fiillerini kullanarak veri alma, sonrası, YERLEŞTİRME veya silme gelmesini REST API'ler, bir dizi açığa WCF veri hizmetleri sağlar. Sunucu tarafında WCF Veri Hizmetleri, yeni OData Hizmetleri oluşturmak için [ASP.NET Web API 'sinin](https://dotnet.microsoft.com/apps/aspnet/apis) yerini almıştır. WCF Veri Hizmetleri istemci kitaplığı, Visual Studio 'dan (**proje &#124; hizmet başvurusu Ekle**) bir .NET uygulamasında OData hizmetlerini kullanmak için iyi bir seçenek olmaya devam etmektedir. Daha fazla bilgi için bkz. [WCF Veri Hizmetleri 4,5](https://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>WCF programlama modeli
 İki varlık arasındaki iletişimi WCF programlama modeline dayanır: bir WCF hizmeti ve bir WCF istemcisi. Programlama modeli, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]<xref:System.ServiceModel> ad alanında kapsüllenir.

#### <a name="wcf-service"></a>WCF Hizmeti
 Bir WCF hizmeti, hizmet ve istemci arasındaki bir sözleşme tanımlayan bir arabirim dayanır. Aşağıdaki kodda gösterildiği gibi bir <xref:System.ServiceModel.ServiceContractAttribute> özniteliğiyle işaretlenir:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Bir WCF hizmeti tarafından sunulan işlevleri veya yöntemleri bir <xref:System.ServiceModel.OperationContractAttribute> özniteliğiyle işaretleyerek tanımlarsınız. Ayrıca, bir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğiyle bileşik bir tür işaretleyerek serileştirilmiş verileri kullanıma sunabilirsiniz. Bu, istemcisinde veri bağlama sağlar.

 Bir arabirim ve metotlarını tanımlandıktan sonra bunlar arabirimi uygulayan bir sınıf içinde kapsüllenir. Tek bir WCF hizmet sınıfı, birden çok hizmet sözleşmelerini uygulayabilirsiniz.

 Bir WCF hizmeti, *uç nokta*olarak bilinen bir şekilde tüketimine sunulur. Uç nokta hizmetiyle iletişim kurmak için tek yolu sağlar. diğer sınıflarla gibi bir doğrudan başvuru hizmetine erişilemiyor.

 Bir uç nokta, adres, bağlama ve bir sözleşme oluşur. Hizmet bulunduğu adresi tanımlar; Bu URL, bir FTP adresi veya ağ ya da yerel yolu olabilir. Bir bağlama hizmeti ile iletişim bir şekilde tanımlar. WCF bağlamaları, HTTP veya FTP, Windows kimlik doğrulaması veya kullanıcı adları ve parolalar gibi bir güvenlik mekanizması gibi bir protokol belirtmek için verimli bir model sağlar ve daha fazlasını. Bir sözleşme WCF hizmet sınıfı tarafından sunulan işlemlerini içerir.

 Birden fazla uç nokta için tek bir WCF hizmet sunulabilir. Bu, farklı şekilde aynı hizmetle iletişim kurmak farklı istemcilerin sağlar. Örneğin, bir bankacılık hizmeti bir uç nokta çalışanlar ve başka bir dış müşteriler için her bağlama, farklı bir adres kullanarak sağlar ve/veya sözleşme.

#### <a name="wcf-client"></a>WCF istemcisi
 WCF istemcisi, bir uygulamanın bir WCF hizmeti ile iletişim kurmasını sağlayan bir *proxy* 'den ve hizmet için tanımlanan bir uç nokta ile eşleşen bir uç noktanın oluşur. Proxy app.config dosyasında istemci tarafında oluşturulur ve hizmet tarafından kullanıma sunulan yöntemleri ve türleri hakkında bilgi içerir. Birden çok uç noktalarını kullanıma Hizmetleri için istemci kendi gereksinimlerini, örneğin, HTTP üzerinden iletişim kurmak ve Windows kimlik doğrulaması kullanmak için en uygun olanı seçebilirsiniz.

 Bir WCF istemcisi oluşturulduktan sonra diğer nesnelerde olduğu gibi kodunuzda hizmete başvuramaz. Örneğin, daha önce gösterilen `GetData` yöntemi çağırmak için aşağıdakine benzer bir kod yazarsınız:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>WCF Visual Studio Araçları
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hem WCF hizmetleri hem de WCF istemcileri oluşturmanıza yardımcı olacak araçlar sağlar. Araçları gösteren bir izlenecek yol için, bkz. [Izlenecek yol: Windows Forms basit BIR WCF hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Oluşturma ve WCF hizmetleri test etme
 Kendi hizmetinizi hızlı bir şekilde oluşturmak için WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablonlarını temel olarak kullanabilirsiniz. Ardından, hata ayıklamak ve hizmeti test etmek için WCF hizmet otomatik konağı ve WCF Test İstemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve kolay bir hata ayıklama ve test döngüsünü sağlamak ve erken bir aşamada bir barındırma modeli için işleme gereksinimini ortadan kaldırır.

#### <a name="wcf-templates"></a>WCF şablonları
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. Çeşitli WCF şablonları **Yeni Proje Ekle** iletişim kutusunda kullanılabilir. Bunlar, WCF hizmet kitaplığı projeleri, WCF Hizmeti Web siteleri ve WCF Hizmeti öğe şablonları içerir.

 Bir şablon seçin, bir hizmet sözleşmesi, hizmet uygulaması ve hizmet yapılandırması için dosyalar eklenir. Hizmet, basit bir "Merhaba Dünya" türünü oluşturma, tüm gerekli özniteliklere zaten eklenir ve kod yazmadan yoktu. Elbette, işlevleri ve gerçek dünya hizmetiniz için yöntemler sağlamak üzere kod eklemek istediğiniz ancak şablonların temel sağlamasıdır.

 WCF şablonları hakkında daha fazla bilgi için bkz. [WCF Visual Studio şablonları](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>WCF hizmet konağı
 Bir WCF hizmeti projesi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata ayıklayıcısını başlattığınızda (F5 tuşuna basarak), hizmeti yerel olarak barındırmak için WCF hizmeti ana bilgisayar aracı otomatik olarak başlatılır. WCF hizmet konağı bir WCF Hizmeti projesini Hizmetleri'nde numaralandırır, projenin yapılandırması yükler ve bulduğu her hizmet için bir ana bilgisayar örneği oluşturur.

 WCF hizmet konağı kullanarak ek kod yazmadan veya belirli bir ana bilgisayara geliştirme sırasında yürüten olmadan bir WCF Hizmeti sınayabilirsiniz.

 WCF hizmet ana bilgisayarı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost. exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>WCF Test İstemcisi
 WCF Test İstemcisi aracı test parametreleri giriş, bir WCF hizmeti için girdi gönderme sağlar ve hizmet geri gönderir yanıtı görüntüleyin. Bu deneyimi ile WCF hizmet konağı birleştirdiğinizde test uygun bir hizmet sağlar. Araç \Common7\IDE klasöründe bulunabilir ve burada Visual Studio 2015, C sürücüsünde yüklü: **C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ common7\ıde\\** .

 Bir WCF Hizmeti projede hata ayıklamak için F5 tuşuna bastığınızda, WCF Test İstemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktaları listesini görüntüler. Test parametreleri ve hizmeti başlatın ve sürekli olarak test edin ve hizmetinizi doğrulamak için bu işlemi yineleyin.

 WCF test Istemcisi hakkında daha fazla bilgi edinmek için bkz. [WCF Test istemcisi (WcfTestClient. exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio'da WCF hizmetlerine erişme
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], WCF istemcileri oluşturma görevini basitleştirir, otomatik olarak bir proxy ve **hizmet başvurusu Ekle** iletişim kutusunu kullanarak eklediğiniz hizmetler için bir uç nokta oluşturur. Tüm gerekli yapılandırma bilgileri, app.config dosyasına eklenir. Çoğu zaman tüm yapmanız gereken olan örneği hizmet kullanmak için.

 **Hizmet başvurusu Ekle** iletişim kutusu, bir hizmetin adresini girmenizi veya çözümünüzde tanımlanan bir hizmeti aramanızı sağlar. İletişim kutusu, hizmetleri ve bu hizmetlerin sunduğu işlemleri listesini döndürür. Ayrıca kod Hizmetleri'nde başvurur ad alanı tanımlamanıza olanak sağlar.

 **Hizmet başvurularını Yapılandır** iletişim kutusu, bir hizmetin yapılandırmasını özelleştirmenizi sağlar. Hizmet adresini değiştirmek, erişim düzeyi, zaman uyumsuz davranış ve ileti anlaşması türleri belirtin ve tür yeniden yapılandırın.

## <a name="how-to-select-a-service-endpoint"></a>Nasıl yapılır: bir hizmet uç noktası seçin
 Bazı Windows Communication Foundation (WCF) Hizmetleri bir istemci hizmeti ile iletişim kurabilir birden çok uç noktalarını kullanıma sunar. Örneğin, bir hizmeti bir HTTP bağlaması ve kullanıcı adını kullanan bir uç nokta kullanıma sunabileceğinize / parola güvenlik ve FTP ve Windows kimlik doğrulaması kullanan ikinci bir uç nokta. İkinci bir intranet üzerinde kullanılabilir ise ilk uç hizmeti bir güvenlik duvarı dışından erişen uygulamalar tarafından kullanılıyor olabilir.

 Böyle bir durumda, bir hizmet başvurusunun oluşturucusuna parametre olarak `endpointConfigurationName` belirtebilirsiniz.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Hizmet uç noktası seçin

1. Çözüm Gezgini ' de proje düğümüne sağ tıklayıp **hizmet başvurusu Ekle** ' yi seçerek bir WCF hizmetine bir başvuru ekleyin

2. Kod Düzenleyicisi'nde hizmet başvurusu için bir oluşturucu ekleyin:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > *ServiceReference* öğesini hizmet başvurusu için ad alanıyla değiştirin ve *Service1Client* değerini hizmetin adıyla değiştirin.

3. Bir IntelliSense listesi için oluşturucu aşırı yüklemeleri ile görüntülenir. `endpointConfigurationName As String` aşırı yüklemeyi seçin.

4. Aşırı yüklemeden sonra, *ConfigurationName* , kullanmak istediğiniz uç noktanın adı olan `=` *ConfigurationName*yazın.

    > [!NOTE]
    > Kullanılabilir uç noktalar adını bilmiyorsanız, app.config dosyasında bulabilirsiniz.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Bir WCF hizmeti için kullanılabilir uç noktalar bulmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu içeren proje için App. config dosyasına sağ tıklayın ve sonra **Aç**' a tıklayın. Dosya Kod düzenleyicisinde görüntülenir.

2. Dosyadaki `<Client>` etiketini arayın.

3. `<Endpoint>`ile başlayan bir etiket için `<Client>` etiketinin altında arama yapın.

     Hizmet başvurusu birden fazla uç nokta sağlıyorsa, iki veya daha fazla `<Endpoint` etiketi olacaktır.

4. `<EndPoint>` etiketinin içinde, bir `name="`*someservice*`"` parametresi bulacaksınız ( *SomeService* bir uç nokta adını temsil eder). Bu, bir hizmet başvurusu için bir oluşturucunun `endpointConfigurationName As String` aşırı yüküne geçirilebilecek olan bitiş noktasının adıdır.

## <a name="how-to-call-a-service-method-asynchronously"></a>Nasıl yapılır: bir hizmet yöntemini zaman uyumsuz olarak çağırma
 Windows Communication Foundation (WCF) hizmetlerini çoğu yöntemleri zaman uyumlu veya zaman uyumsuz olarak çağrılabilir. Zaman uyumsuz bir yöntemi çağırmak uygulamanızın yavaş bir bağlantı üzerinden çalıştığında yöntemi Aranan çalışmaya devam olanak tanır.

 Bir hizmet başvurusu için bir proje eklendiğinde varsayılan olarak, zaman uyumlu yöntemleri çağırmak için yapılandırılır. **Hizmet başvurusunu Yapılandır** iletişim kutusunda bir ayarı değiştirerek yöntemleri zaman uyumsuz olarak çağırma davranışını değiştirebilirsiniz.

> [!NOTE]
> Bu seçenek, bir hizmet başına temelinde ayarlanır. Zaman uyumsuz olarak bir hizmet için bir yöntem çağrılırsa, tüm yöntemlerin zaman uyumsuz olarak çağrılmalıdır.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Bir hizmet yöntemini zaman uyumsuz olarak çağırma

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurusunu Yapılandır** iletişim kutusunda, **zaman uyumsuz işlemler oluştur** onay kutusunu seçin.

## <a name="how-to-bind-data-returned-by-a-service"></a>Nasıl yapılır: bir hizmet tarafından döndürülen veri bağlama
 Yalnızca bir denetim için herhangi bir veri kaynağını bağlayabilirsiniz gibi bir denetim için bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen veriler bağlayabilirsiniz. WCF hizmetine bir başvuru eklediğinizde, hizmet verileri döndüren bileşik türler içeriyorsa, bunlar otomatik olarak **veri kaynakları** penceresine eklenir.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen tek bir veri alanı denetim Bağlanılacak

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın. **Veri kaynakları** penceresi görüntülenir.

2. **Veri kaynakları** penceresinde, hizmet başvurunuz için düğümü genişletin. Hizmet tarafından döndürülen herhangi bir bileşik türler görüntülenir.

3. Bir tür için bir düğümünü genişletin. Bu tür için veri alanları görüntülenir.

4. Bir alan seçin ve veri türü için uygun olan denetimler listesini görüntülemek için açılan oka tıklayın.

5. Bağlamak istediğiniz denetim türünü tıklayın.

6. Alanı form üzerine sürükleyin. Denetim, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeniyle birlikte forma eklenir.

7. 6 herhangi diğer alanları ancak 4 arasındaki adımları yineleyin bağlamak istediğiniz.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen bileşik türü bir denetim Bağlanılacak

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin. **Veri kaynakları** penceresi görüntülenir.

2. **Veri kaynakları** penceresinde, hizmet başvurunuz için düğümü genişletin. Hizmet tarafından döndürülen herhangi bir bileşik türler görüntülenir.

3. Bir tür için bir düğüm seçin ve kullanılabilir seçeneklerin bir listesini görüntülemek için açılan oka tıklayın.

4. Verileri ayrı denetimlerde göstermek için DataGridView veya **Details** içindeki verileri göstermek için **DataGridView** ' e tıklayın.

5. Düğümü form üzerine sürükleyin. Denetimler, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeniyle birlikte forma eklenir.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Nasıl yapılır: Varolan türleri yeniden kullan bir hizmetini yapılandırma
 Bir hizmet başvurusu için bir proje eklendiğinde, hizmette tanımlanan herhangi bir türü yerel projede oluşturulur. Çoğu durumda bu, bir hizmet ortak [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] türlerini kullandığında veya türler paylaşılan bir kitaplıkta tanımlandığında yinelenen türler oluşturur.

 Bu sorunu önlemek için bütünleştirilmiş kodlardaki türleri varsayılan olarak paylaşılır. Bir veya daha fazla derleme için tür paylaşımını devre dışı bırakmak istiyorsanız, **Hizmet başvurularını Yapılandır** iletişim kutusunda bunu yapabilirsiniz.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Tek bir bütünleştirilmiş kod paylaşımı türü devre dışı bırakmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurularını Yapılandır** iletişim kutusunda, **belirtilen başvurulan derlemelerdeki türleri yeniden kullan**' ı seçin.

4. Tür paylaşımını etkinleştirmek istediğiniz her derleme için onay kutusunu seçin. Bir derleme için paylaşım türü devre dışı bırakmak için onay kutusunu temizleyin.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Tüm derlemelerde paylaşım türü devre dışı bırakmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurularını Yapılandır** iletişim kutusunda, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu temizleyin.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'de WCF Hizmetleri oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar.|
|[İzlenecek Yol: WPF ve Entity Framework ile WCF Veri Hizmeti Oluşturma](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)][!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar.|
|[WCF Geliştirme Araçlarını Kullanma](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'de WCF Hizmetleri oluşturma ve test etme işlemlerinin nasıl yapılacağını açıklar.|
|[Nasıl yapılır: hizmet başvurusu ekleme, güncelleştirme veya kaldırma](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Ekleme, güncelleştirme veya WCF hizmetleri projeden açıklar.|
|[Nasıl Yapılır: WCF Veri Hizmeti Başvurusunu Güncelleme veya Kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)][!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] nasıl başvurulacağını ve kullanılacağını açıklar.|
|[Hizmet Başvurularında Sorun Giderme](../data-tools/troubleshooting-service-references.md)|Hizmet başvuruları ve bunların nasıl ile ortaya çıkabilecek bazı yaygın hatalar gösterir.|
|[WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)|Genel hata ayıklama sorunları ve WCF hizmetlerinde hata ayıklama sırasında karşılaşabileceğiniz teknikleri açıklar.|
|[Windows Communication Foundation kimlik doğrulama hizmetine genel bakış](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|WCF Web sitesi için bir rol hizmeti sağlamak için nasıl kullanılacağını açıklar.|
|[İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Türü belirtilmiş veri kümesi oluşturma ve birden çok projelere TableAdapter ve veri kümesi kodunu ayırmak için adım adım yönergeler sağlar.|
|[Hizmet Başvurusu Yapılandır İletişim Kutusu](../data-tools/configure-service-reference-dialog-box.md)|**Hizmet başvurusunu Yapılandır** iletişim kutusunun Kullanıcı arabirimi öğelerini açıklar.|

## <a name="reference"></a>Başvuru
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
