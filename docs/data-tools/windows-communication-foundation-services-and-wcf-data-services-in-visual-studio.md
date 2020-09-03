---
title: Windows Communication Foundation ve WCF Veri Hizmetleri
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- VB
- CSharp
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c1f24a33a482b1994d0d8667b4fc71cf968e4625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281051"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri

Visual Studio, dağıtılmış uygulamalar oluşturmaya yönelik Windows Communication Foundation (WCF) ve WCF Veri Hizmetleri, Microsoft teknolojileri ile çalışmaya yönelik araçlar sağlar. Bu konu, Visual Studio perspektifinden hizmetlere giriş sağlar. Tüm belgeler için bkz. [WCF Veri Hizmetleri 4,5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>WCF nedir?

Windows Communication Foundation (WCF), güvenli, güvenilir, işlem temelli ve birlikte çalışabilen dağıtılmış uygulamalar oluşturmaya yönelik Birleşik bir çerçevedir. ASMX Web Hizmetleri, .NET Remoting, Enterprise Services (DCOM) ve MSMQ gibi eski işlemler arası iletişim teknolojilerinin yerini alır. WCF, birleştirilmiş bir programlama modeli altındaki tüm teknolojilerin işlevlerini birlikte getirir. Bu, dağıtılmış uygulamalar geliştirme deneyimini basitleştirir.

### <a name="what-are-wcf-data-services"></a>WCF Veri Hizmetleri nedir?

WCF Veri Hizmetleri, açık veri (OData) protokolü standardının bir uygulamasıdır.  WCF Veri Hizmetleri, tablo verilerini bir dizi REST API 'si olarak kullanıma sunmanızı sağlayarak GET, POST, PUT veya DELETE gibi standart HTTP fiillerini kullanarak veri döndürmenize olanak tanır. Sunucu tarafında WCF Veri Hizmetleri, yeni OData Hizmetleri oluşturmak için [ASP.NET Web API 'sinin](https://dotnet.microsoft.com/apps/aspnet/apis) yerini almıştır. WCF veri Hizmetleri istemci kitaplığı, Visual Studio 'dan (**Proje**  >  **hizmet başvurusu Ekle**) bir .NET uygulamasında OData hizmetlerini kullanmak için iyi bir seçenek olmaya devam etmektedir. Daha fazla bilgi için bkz. [WCF Veri Hizmetleri 4,5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>WCF programlama modeli

WCF programlama modeli iki varlık arasındaki iletişimi temel alır: bir WCF hizmeti ve WCF istemcisi. Programlama modeli <xref:System.ServiceModel> .net 'teki ad alanı içinde kapsüllenir.

### <a name="wcf-service"></a>WCF hizmeti

WCF hizmeti, hizmet ile istemci arasında bir sözleşmeyi tanımlayan arabirimi temel alır. <xref:System.ServiceModel.ServiceContractAttribute>Aşağıdaki kodda gösterildiği gibi bir özniteliğiyle işaretlenir:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Bir WCF hizmeti tarafından sunulan işlevleri veya yöntemleri bir özniteliğiyle işaretleyerek tanımlarsınız <xref:System.ServiceModel.OperationContractAttribute> .

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Ayrıca, bir öznitelik ile bileşik bir tür işaretleyerek serileştirilmiş verileri kullanıma sunabilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> . Bu, bir istemcide veri bağlamayı mümkün bir şekilde sunar.

Bir arabirim ve yöntemleri tanımlandıktan sonra, arabirimini uygulayan bir sınıfta kapsüllenir. Tek bir WCF hizmeti sınıfı, birden çok hizmet sözleşmesi uygulayabilir.

Bir WCF hizmeti, *uç nokta*olarak bilinen bir şekilde tüketimine sunulur. Uç nokta, hizmetle iletişim kurmanın tek yolunu sağlar; diğer sınıflarla yaptığınız gibi doğrudan başvuru aracılığıyla hizmete erişemezsiniz.

Bir uç nokta, bir adres, bağlama ve bir anlaşmada oluşur. Adres, hizmetin nerede olduğunu tanımlar; Bu bir URL, FTP adresi veya ağ ya da yerel yol olabilir. Bağlama, hizmetle iletişim kurma şeklini tanımlar. WCF bağlamaları, HTTP veya FTP gibi bir protokol ve Windows kimlik doğrulaması, Kullanıcı adları ve parolalar gibi bir güvenlik mekanizması ve çok daha fazlasını belirtmek için çok yönlü bir model sağlar. Bir sözleşme, WCF hizmet sınıfı tarafından sunulan işlemleri içerir.

Tek bir WCF hizmeti için birden fazla uç nokta sunulabilir. Bu, farklı istemcilerin aynı hizmetle farklı yollarla iletişim kurmasını sağlar. Örneğin, bir bankacılık hizmeti çalışanlar için bir uç nokta ve her biri farklı bir adres, bağlama ve/veya sözleşme kullanan harici müşteriler için bir uç nokta sağlayabilir.

### <a name="wcf-client"></a>WCF istemcisi

WCF istemcisi, bir uygulamanın bir WCF hizmeti ile iletişim kurmasını sağlayan bir *proxy* 'den ve hizmet için tanımlanan bir uç nokta ile eşleşen bir uç noktanın oluşur. Proxy *app.config* dosyadaki istemci tarafında oluşturulur ve hizmet tarafından açığa çıkarılan türler ve yöntemler hakkında bilgiler içerir. Birden çok bitiş noktası sunan hizmetler için, istemci, HTTP üzerinden iletişim kurmak ve Windows kimlik doğrulamasını kullanmak gibi, ihtiyaçlarına en uygun olanı seçebilir.

Bir WCF istemcisi oluşturulduktan sonra, kodunuzun içindeki hizmete tıpkı diğer herhangi bir nesne gibi başvurabilirsiniz. Örneğin, `GetData` daha önce gösterilen yöntemi çağırmak için aşağıdakine benzer bir kod yazarsınız:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 'da WCF araçları

Visual Studio, WCF Hizmetleri ve WCF istemcileri oluşturmanıza yardımcı olacak araçlar sağlar. Araçları gösteren bir izlenecek yol için, bkz. [Izlenecek yol: Windows Forms basit BIR WCF hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>WCF Hizmetleri oluşturma ve test etme

Kendi hizmetinizi hızlı bir şekilde oluşturmak için WCF Visual Studio şablonlarını bir temel olarak kullanabilirsiniz. Ardından, hizmet hatalarını ayıklamak ve test etmek için WCF hizmeti otomatik ana bilgisayarı ve WCF test Istemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve kullanışlı bir hata ayıklama ve test çevrimi sağlar ve bir barındırma modeline erken bir aşamada yürütülmesi gereksinimini ortadan kaldırır.

#### <a name="wcf-templates"></a>WCF şablonları

WCF Visual Studio şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. Çeşitli WCF şablonları **Yeni Proje Ekle** iletişim kutusunda kullanılabilir. Bunlar WCF hizmeti lLibrary projelerini, WCF hizmeti Web sitelerini ve WCF hizmeti öğe şablonlarını içerir.

Bir şablon seçtiğinizde, bir hizmet sözleşmesi, hizmet uygulama ve hizmet yapılandırması için dosyalar eklenir. Tüm gerekli öznitelikler zaten eklendi, basit bir "Merhaba Dünya" hizmet türü oluşturuyor ve herhangi bir kod yazmak zorunda değilsiniz. Kuşkusuz, gerçek dünya hizmetiniz için işlevler ve Yöntemler sağlamak üzere kod eklemek isteyeceksiniz, ancak şablonlar temel temeli sağlar.

WCF şablonları hakkında daha fazla bilgi için bkz. [WCF Visual Studio şablonları](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>WCF hizmet ana bilgisayarı

Bir WCF hizmeti projesi için Visual Studio hata ayıklayıcısını başlattığınızda ( **F5**tuşuna basarak), hizmeti yerel olarak BARıNDıRMAK Için WCF hizmeti ana bilgisayar aracı otomatik olarak başlatılır. WCF hizmeti ana bilgisayarı bir WCF hizmeti projesindeki Hizmetleri numaralandırır, projenin yapılandırmasını yükler ve bulduğu her hizmet için bir konak başlatır.

WCF hizmeti ana bilgisayarı kullanarak, ek kod yazmadan veya geliştirme sırasında belirli bir konağa işlemeden bir WCF hizmetini test edebilirsiniz.

WCF hizmet ana bilgisayarı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>WCF Test istemcisi

WCF test Istemcisi Aracı, test parametreleri girmenizi, bu girişi bir WCF hizmetine göndermenizi ve hizmetin geri gönderdiği yanıtı görüntülemenizi sağlar. WCF hizmet ana bilgisayarı ile birleştirdiğinizde uygun bir hizmet testi deneyimi sağlar. Aracı *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* klasöründe bulun.

WCF hizmeti projesinde hata ayıklamak için **F5** tuşuna BASTıĞıNıZDA, WCF Test istemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktalarının bir listesini görüntüler. Parametreleri test edebilir ve hizmeti başlatabilir ve hizmetinizi sürekli olarak test etmek ve doğrulamak için bu işlemi yineleyebilirsiniz.

WCF test Istemcisi hakkında daha fazla bilgi için bkz. [WCF Test istemcisi (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio 'da WCF hizmetlerine erişme

Visual Studio, WCF istemcileri oluşturma görevini basitleştirir, otomatik olarak bir ara sunucu ve **hizmet başvurusu Ekle** iletişim kutusunu kullanarak eklediğiniz hizmetler için bir uç nokta oluşturur. Tüm gerekli yapılandırma bilgileri *app.config* dosyasına eklenir. Çoğu zaman tüm yapmanız gereken, hizmeti kullanmak için örnekleyebilirsiniz.

**Hizmet başvurusu Ekle** iletişim kutusu, bir hizmetin adresini girmenizi veya çözümünüzde tanımlanan bir hizmeti aramanızı sağlar. İletişim kutusu, hizmetlerin ve bu hizmetler tarafından sunulan işlemlerin bir listesini döndürür. Ayrıca, koddaki hizmetlere başvurmayacak ad alanını tanımlamanızı sağlar.

**Hizmet başvurularını Yapılandır** iletişim kutusu, bir hizmetin yapılandırmasını özelleştirmenizi sağlar. Bir hizmetin adresini değiştirebilir, erişim düzeyi, zaman uyumsuz davranış ve ileti sözleşme türlerini belirtebilir ve tür yeniden kullanımını yapılandırabilirsiniz.

## <a name="how-to-select-a-service-endpoint"></a>Nasıl yapılır: hizmet uç noktası seçme

Bazı Windows Communication Foundation (WCF) Hizmetleri, bir istemcinin hizmetle iletişim kurabildiği birden çok uç noktasını kullanıma sunar. Örneğin, bir hizmet, bir HTTP bağlaması ve Kullanıcı adı ve parola güvenliği kullanan bir uç nokta ve FTP ve Windows kimlik doğrulaması kullanan ikinci bir uç nokta açığa çıkabilir. İlk uç nokta, hizmete bir güvenlik duvarı dışından erişen uygulamalar tarafından kullanılabilir, ikincisi ise bir intranette kullanılabilir.

Böyle bir durumda, `endpointConfigurationName` hizmet başvurusu için oluşturucuya parametre olarak belirtebilirsiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Hizmet uç noktası seçmek için

1. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **hizmet başvurusu Ekle**' yi seçerek bir WCF hizmetine bir başvuru ekleyin.

2. Kod düzenleyicisinde, hizmet başvurusu için bir Oluşturucu ekleyin:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > *ServiceReference* öğesini hizmet başvurusu için ad alanıyla değiştirin ve *Service1Client* değerini hizmetin adıyla değiştirin.

3. Oluşturucunun aşırı yüklerini içeren bir IntelliSense listesi görüntülenir. `endpointConfigurationName As String`Aşırı yüklemeyi seçin.

4. Aşırı yüklemeden sonra, `=` *ConfigurationName* , kullanmak istediğiniz uç noktanın adı olan *ConfigurationName*yazın.

    > [!NOTE]
    > Kullanılabilir uç noktaların adlarını bilinmediğinizde, *app.config* dosyasında bulabilirsiniz.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Bir WCF hizmeti için kullanılabilir uç noktaları bulmak için

1. **Çözüm Gezgini**, hizmet başvurusunu içeren proje için **app.config** dosyasına sağ tıklayın ve sonra **Aç**' a tıklayın. Dosya kod düzenleyicisinde görünür.

2. `<Client>`Dosyadaki etiketi arayın.

3. `<Client>`İle başlayan bir etiket için etiketinin altında arama yapın `<Endpoint>` .

     Hizmet başvurusu birden fazla uç nokta sağlıyorsa, iki veya daha fazla etiket olur `<Endpoint` .

4. Etiketinin içinde `<EndPoint>` , bir `name="` *SomeService* `"` parametresi ( *SomeService* 'in bir uç nokta adını temsil ettiği) bulacaksınız. Bu, `endpointConfigurationName As String` bir hizmet başvurusu için bir oluşturucunun aşırı yüküne geçirilebileceğini belirten bitiş noktası adıdır.

## <a name="how-to-call-a-service-method-asynchronously"></a>Nasıl yapılır: bir hizmet yöntemini zaman uyumsuz olarak çağırma

Windows Communication Foundation (WCF) hizmetlerindeki yöntemlerin çoğu, zaman uyumlu veya zaman uyumsuz olarak çağrılabilir. Yöntemi zaman uyumsuz olarak çağırmak, yavaş bir bağlantı üzerinden çalışırken yöntem çağrıldığında uygulamanızın çalışmaya devam etmesini sağlar.

Varsayılan olarak, bir projeye bir hizmet başvurusu eklendiğinde, yöntemleri zaman uyumlu olarak çağırmak üzere yapılandırılır. **Hizmet başvurusunu Yapılandır** iletişim kutusunda bir ayarı değiştirerek yöntemleri zaman uyumsuz olarak çağırma davranışını değiştirebilirsiniz.

> [!NOTE]
> Bu seçenek hizmet başına temelinde ayarlanır. Bir hizmet için bir yöntem zaman uyumsuz olarak çağrılırsa, tüm yöntemler zaman uyumsuz olarak çağrılmalıdır.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Bir hizmet yöntemini zaman uyumsuz olarak çağırmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurusunu Yapılandır** iletişim kutusunda, **zaman uyumsuz işlemler oluştur** onay kutusunu seçin.

## <a name="how-to-bind-data-returned-by-a-service"></a>Nasıl yapılır: bir hizmet tarafından döndürülen verileri bağlama

Bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verileri, başka bir veri kaynağını bir denetime bağlayacağınız gibi bir denetime bağlayabilirsiniz. WCF hizmetine bir başvuru eklediğinizde, hizmet verileri döndüren bileşik türler içeriyorsa, bunlar otomatik olarak **veri kaynakları** penceresine eklenir.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen tek veri alanına bir denetim bağlamak için

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

   **Veri kaynakları** penceresi görüntülenir.

2. **Veri kaynakları** penceresinde, hizmet başvurunuz için düğümü genişletin. Hizmet görüntüsü tarafından döndürülen bileşik türler.

3. Bir tür için düğüm genişletin. Bu tür için veri alanları görüntülenir.

4. Bir alan seçin ve veri türü için kullanılabilen denetimlerin listesini göstermek için aşağı açılan oka tıklayın.

5. Bağlamak istediğiniz denetim türüne tıklayın.

6. Alanı bir formun üzerine sürükleyin. Denetim, bir <xref:System.Windows.Forms.BindingSource> bileşen ve bileşenle birlikte formuna eklenir <xref:System.Windows.Forms.BindingNavigator> .

7. Bağlamak istediğiniz diğer alanlar için 4 ile 6 arasındaki adımları yineleyin.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF hizmeti tarafından döndürülen bileşik türe bir denetim bağlamak için

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin. **Veri kaynakları** penceresi görüntülenir.

2. **Veri kaynakları** penceresinde, hizmet başvurunuz için düğümü genişletin. Hizmet görüntüsü tarafından döndürülen bileşik türler.

3. Bir tür için düğüm seçin ve kullanılabilir seçeneklerin listesini göstermek için aşağı açılan oka tıklayın.

4. Verileri ayrı denetimlerde göstermek için DataGridView veya **Details** içindeki verileri göstermek için **DataGridView** ' e tıklayın.

5. Düğümü formun üzerine sürükleyin. Denetimler, bir <xref:System.Windows.Forms.BindingSource> bileşen ve bileşenle birlikte formuna eklenir <xref:System.Windows.Forms.BindingNavigator> .

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Nasıl yapılır: mevcut türleri yeniden kullanmak için bir hizmet yapılandırma

Bir projeye hizmet başvurusu eklendiğinde, hizmette tanımlı türler yerel projede oluşturulur. Çoğu durumda bu, bir hizmet ortak .NET türlerini kullandığında veya türler paylaşılan bir kitaplıkta tanımlandığında yinelenen türler oluşturur.

Bu sorundan kaçınmak için, başvurulan derlemelerdeki türler varsayılan olarak paylaşılır. Bir veya daha fazla derleme için tür paylaşımını devre dışı bırakmak istiyorsanız, **Hizmet başvurularını Yapılandır** iletişim kutusunda bunu yapabilirsiniz.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Tek bir derlemede tür paylaşımını devre dışı bırakmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurularını Yapılandır** iletişim kutusunda, **belirtilen başvurulan derlemelerdeki türleri yeniden kullan**' ı seçin.

4. Tür paylaşımını etkinleştirmek istediğiniz her derleme için onay kutusunu seçin. Bir derlemenin tür paylaşımını devre dışı bırakmak için onay kutusunu işaretsiz bırakın.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Tüm derlemelerde tür paylaşımını devre dışı bırakmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu seçin.

2. **Proje** menüsünde, **hizmet başvurusunu Yapılandır**' ı tıklatın.

3. **Hizmet başvurularını Yapılandır** iletişim kutusunda, **başvurulan derlemelerde türleri yeniden kullan** onay kutusunu temizleyin.

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Visual Studio 'da WCF Hizmetleri oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar. |
| [İzlenecek yol: WPF ve Entity Framework bir WCF veri hizmeti oluşturma](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Visual Studio 'da WCF Veri Hizmetleri oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar. |
| [WCF geliştirme araçlarını kullanma](/dotnet/framework/wcf/using-the-wcf-development-tools) | Visual Studio 'da WCF hizmetlerinin nasıl oluşturulduğunu ve test yapıldığını açıklar. |
| | [Nasıl yapılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Hizmet başvurularının sorunlarını giderme](../data-tools/troubleshooting-service-references.md) | Hizmet başvurularıyla oluşabilecek bazı yaygın hataları ve bunların nasıl önleyebileceğini gösterir. |
| [WCF hizmetlerinde hata ayıklama](../debugger/debugging-wcf-services.md) | WCF hizmetlerinde hata ayıklarken karşılaşabileceğiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar. |
| [İzlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Türü belirtilmiş bir veri kümesi oluşturmak ve TableAdapter ve dataset kodunu birden çok projeye ayırmak için adım adım yönergeler sağlar. |
| [Hizmet başvurusunu yapılandırma iletişim kutusu](../data-tools/configure-service-reference-dialog-box.md) | **Hizmet başvurusunu Yapılandır** iletişim kutusunun Kullanıcı arabirimi öğelerini açıklar. |

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
