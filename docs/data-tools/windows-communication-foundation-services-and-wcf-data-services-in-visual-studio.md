---
title: Windows Communication Foundation ve WCF Veri Hizmetleri
description: Dağıtılmış uygulamalar Windows için communication foundation (WCF) hizmetleri WCF Veri Hizmetleri Visual Studio'leri keşfedin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 754f2b08f73b111ed8f62dedde17e2c133565d0a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631022"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri

Visual Studio, dağıtılmış uygulamalar oluşturmak için microsoft Windows Communication Foundation (WCF) ve WCF Veri Hizmetleri ile çalışmaya yardımcı olacak araçlar sağlar. Bu konu, hizmetlere genel bakış açısından Visual Studio sağlar. Tüm belgeler için bkz. [WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>WCF nedir?

Windows Communication Foundation (WCF), güvenli, güvenilir, işlem yapılan ve birlikte çalışabilen dağıtılmış uygulamalar oluşturmak için birleştirilmiş bir çerçevedir. ASMX web hizmetleri, .NET İletişimi, Enterprise Hizmetleri (DCOM) ve MSMQ gibi eski işlemler arası iletişim teknolojilerinin yerini almaktadır. WCF, tüm bu teknolojilerin işlevselliğini birleştirilmiş bir programlama modeli altında bir araya getirir. Bu, dağıtılmış uygulamalar geliştirme deneyimini kolaylaştırır.

### <a name="what-are-wcf-data-services"></a>Hangi WCF Veri Hizmetleri

WCF Veri Hizmetleri, Açık Veri (OData) Protokolü standardını bir uygulamadır.  WCF Veri Hizmetleri, tablo verilerini REST API'leri kümesi olarak ortaya çıkarmanıza olanak sağlayarak GET, POST, PUT veya DELETE gibi standart HTTP fiillerini kullanarak veri geri dönmenizi sağlar. Sunucu tarafında, WCF Veri Hizmetleri OData hizmetleri oluşturmak için [ASP.NET Web API'si](https://dotnet.microsoft.com/apps/aspnet/apis) tarafından yenisi yapılıyor. İstemci WCF Veri Hizmetleri kitaplığı, bir .NET uygulamasındaki OData hizmetlerini Visual Studio ' den ( Project Hizmet Başvurusu Ekle) tüketmek için iyi **bir**  >  **seçenektir.** Daha fazla bilgi için [bkz. WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>WCF programlama modeli

WCF programlama modeli iki varlık arasındaki iletişimi temel alarak kullanılır: WCF hizmeti ve WCF istemcisi. Programlama modeli . NET'te ad <xref:System.ServiceModel> alanına kapsüller.

### <a name="wcf-service"></a>WCF Hizmeti

WCF hizmeti, hizmetle istemci arasındaki sözleşmeyi tanımlayan bir arabirime dayalıdır. Aşağıdaki kodda <xref:System.ServiceModel.ServiceContractAttribute> gösterildiği gibi bir özniteliğiyle işaretlenir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet6":::

Bir WCF hizmeti tarafından ortaya çıkacak işlevleri veya yöntemleri bir öznitelikle işaretleyerek <xref:System.ServiceModel.OperationContractAttribute> tanımlarsiniz.

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

Ayrıca, bileşik türü bir öznitelikle işaretleyerek serileştirilmiş verileri açığa <xref:System.Runtime.Serialization.DataContractAttribute> çıkarabilirsiniz. Bu, istemcide veri bağlamayı sağlar.

Bir arabirim ve yöntemleri tanımlandığı zaman, bunlar arabirimi uygulayan bir sınıfta kapsüller. Tek bir WCF hizmet sınıfı birden çok hizmet sözleşmesi uygulama.

WCF hizmeti, uç nokta olarak bilinen aracılığıyla tüketim için *açığa çıkar.* Uç nokta, hizmetle iletişim kurmanın tek yolunu sağlar; hizmete diğer sınıflarda olduğu gibi doğrudan bir başvuru aracılığıyla erişesiniz.

Uç nokta bir adres, bağlama ve sözleşmeden oluşur. Adres, hizmetin bulunduğu yeri tanımlar; Bu bir URL, FTP adresi veya ağ ya da yerel yol olabilir. Bağlama, hizmetle iletişim kurma yolunu tanımlar. WCF bağlamaları HTTP veya FTP gibi bir protokolü, Windows Kimlik Doğrulaması gibi bir güvenlik mekanizmasını veya kullanıcı adlarını ve parolalarını ve daha fazlasını belirtmek için çok yönlü bir model sağlar. Sözleşme, WCF hizmet sınıfı tarafından ortaya çıkarılma işlemlerini içerir.

Tek bir WCF hizmeti için birden çok uç nokta kullanılabilir. Bu, farklı istemcilerin aynı hizmetle farklı yollarla iletişim kurmasına olanak sağlar. Örneğin, bir bankacılık hizmeti çalışanlar için bir uç nokta ve her biri farklı bir adres, bağlama ve/veya sözleşme kullanan dış müşteriler için başka bir uç nokta sağlar.

### <a name="wcf-client"></a>WCF istemcisi

WCF istemcisi, bir uygulamanın BIR WCF hizmetiyle iletişim kurmasına olanak sağlayan bir *ara* sunucudan ve hizmet için tanımlanan bir uç noktayla eşleşen bir uç noktadan oluşur. Ara sunucu,app.configdosyasında istemci  tarafında oluşturulur ve hizmet tarafından ortaya çıkacak türler ve yöntemler hakkında bilgi içerir. Birden çok uç noktayı açığa çıkaran hizmetler için, istemci HTTP üzerinden iletişim kurmak ve Kimlik Doğrulaması'Windows kullanabilir.

WcF istemcisi oluşturulduktan sonra, kodundaki hizmete diğer nesneler gibi başvurabilirsiniz. Örneğin, daha önce `GetData` gösterilen yöntemini çağırmanız için aşağıdakine benzer bir kod yazmanız gerekir:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio'de WCF araçları

Visual Studio hem WCF hizmetleri hem de WCF istemcileri oluşturmanıza yardımcı olacak araçlar sağlar. Araçları gösteren bir izlenecek yol için bkz. [Walkthrough: Creating a simple WCF service in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>WCF hizmetleri oluşturma ve test

Kendi hizmetinizi hızlı bir Visual Studio için WCF şablonlarını temel olarak kullanabilirsiniz. Ardından, hizmette hata ayıklamak ve test etmek için WCF Hizmeti Otomatik Ana Bilgisayarı ve WCF Test İstemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve kullanışlı bir hata ayıklama ve test döngüsü sağlar ve bir barındırma modeline erken aşamada işleme gereksinimini ortadan kaldırmaya yardımcı olur.

#### <a name="wcf-templates"></a>WCF Şablonları

WCF Visual Studio şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. Yeni Uygulama Ekle iletişim kutusunda birkaç WCF **Project** vardır. Bunlar WCF hizmeti lLibrary projeleri, WCF hizmeti web siteleri ve WCF Hizmeti öğe şablonlarıdır.

Bir şablon seçerek hizmet sözleşmesi, hizmet uygulaması ve hizmet yapılandırması için dosyalar eklenir. Tüm gerekli öznitelikler zaten eklenmiştir, basit bir "Merhaba Dünya" hizmet türü oluşturulur ve herhangi bir kod yazmanız gerekmez. Elbette gerçek dünya hizmetiniz için işlevler ve yöntemler sağlamak için kod eklemek istersiniz, ancak şablonlar temel temeli sağlar.

WCF şablonları hakkında daha fazla bilgi edinmek için bkz. [WCF Visual Studio şablonları.](/dotnet/framework/wcf/wcf-vs-templates)

#### <a name="wcf-service-host"></a>WCF hizmet ana bilgisayarı

Bir WCF hizmet projesi için Visual Studio hata ayıklayıcısını **(F5** tuşuna basarak) başlarken, WCF Hizmet Ana Bilgisayarı aracı hizmeti yerel olarak barındırmak için otomatik olarak başlatılır. WCF Hizmet Ana Bilgisayarı bir WCF hizmet projesinin hizmetlerini numaralandırarak projenin yapılandırmasını yükler ve bulduğu her hizmet için bir konak örneği sunar.

WCF Hizmet Ana Bilgisayarı kullanarak, bir WCF hizmetini geliştirme sırasında ek kod yazmadan veya belirli bir ana bilgisayarla işlemeden test etmek için kullanabilirsiniz.

WCF Hizmet Ana Bilgisayarı hakkında daha fazla bilgi edinmek için bkz. [WCF hizmet WcfSvcHost.exe .](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)

#### <a name="wcf-test-client"></a>WCF test istemcisi

WCF Test İstemcisi aracı, test parametrelerini girebilirsiniz, bu girişi bir WCF hizmetine gönderir ve hizmetin geri gönderdiği yanıtı görüntüebilirsiniz. WCF Hizmet Ana Bilgisayarı ile birleştirip kullanışlı bir hizmet testi deneyimi sağlar. *Aracı %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE klasöründe* bulun.

WCF hizmet projesinde hata ayıklamak için **F5** tuşuna basıyorsanız, WCF Test İstemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktalarının listesini görüntüler. Parametreleri test etmek ve hizmeti başlatmak ve hizmetinizi sürekli test etmek ve doğrulamak için bu işlemi tekrarlayın.

WCF Test İstemcisi hakkında daha fazla bilgi edinmek için bkz. [WCF test istemcisi (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio'de WCF Visual Studio

Visual Studio, WCF istemcileri oluşturma görevini basitleştirerek, ağ iletişim kutusunu kullanarak, otomatik olarak bir ara sunucu **ve Hizmet Başvurusu Ekle** eklersiniz. Tüm gerekli yapılandırma bilgileriapp.config *eklenir.* Çoğu zaman, hizmeti kullanmak için tek gereken hizmeti örneği olarak kullanmaktır.

Bu **Hizmet Başvurusu Ekle** iletişim kutusu, bir hizmetin adresini girmenize veya çözümünüzde tanımlanan bir hizmeti aramanıza olanak sağlar. İletişim kutusu, hizmetlerin ve bu hizmetler tarafından sağlanan işlemlerin listesini döndürür. Ayrıca kodda hizmetlere başvuracakları ad alanını tanımlamanız da sağlar.

Hizmet **Başvurularını Yapılandır** iletişim kutusu, bir hizmet için yapılandırmayı özelleştirmenize olanak sağlar. Bir hizmetin adresini değiştirebilir, erişim düzeyini, zaman uyumsuz davranışı ve ileti sözleşmesi türlerini belirterek türü yeniden yapılandırabilirsiniz.

## <a name="how-to-select-a-service-endpoint"></a>Nasıl: Hizmet uç noktası seçme

Bazı Windows Communication Foundation (WCF) hizmetleri, istemcinin hizmetle iletişim kurarak iletişim kurarak birden çok uç noktayı ortaya çıkarır. Örneğin, bir hizmet HTTP bağlaması ve kullanıcı adı ile parola güvenliği kullanan bir uç noktayı ve FTP ve Kimlik Doğrulaması kullanan ikinci bir uç noktayı Windows olabilir. İlk uç nokta, hizmete güvenlik duvarı dışından erişen uygulamalar tarafından, ikinci uç nokta ise intranette kullanılabilir.

Böyle bir durumda, bir hizmet başvurusu `endpointConfigurationName` için oluşturucu için parametresi olarak belirtebilirsiniz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Bir hizmet uç noktası seçmek için

1. Içinde proje düğümüne sağ tıklar ve Hizmet  başvurusu ekle'yi Çözüm Gezgini WCF **hizmetine başvuru ekleyin.**

2. Kod Düzenleyicisi'nde hizmet başvurusu için bir oluşturucu ekleyin:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > *ServiceReference yerine* hizmet başvurusu için ad alanını, *Service1Client* alanını ise hizmetin adıyla değiştirin.

3. Oluşturucu için aşırı yüklemeleri içeren bir IntelliSense listesi görüntülenir. Aşırı yüklemeyi `endpointConfigurationName As String` seçin.

4. Aşırı yüklemeyi takip eden `=` *ConfigurationName yazın;* burada *ConfigurationName,* kullanmak istediğiniz uç noktanın adıdır.

    > [!NOTE]
    > Kullanılabilir uç noktaların adlarını bilmiyorsanız, bunlarıapp.config *bulabilirsiniz.*

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF hizmeti için kullanılabilir uç noktaları bulmak için

1. Bu **Çözüm Gezgini,** hizmet başvurus **app.config** proje için dosya dosyasına sağ tıklayın ve ardından Aç'a **tıklayın.** Dosya Kod Düzenleyicisi'nde görünür.

2. Dosyada `<Client>` etiketini ara.

3. etiketinin `<Client>` altında ile başlayan bir etiket için arama. `<Endpoint>`

     Hizmet başvurusu birden çok uç nokta sağlarsa, iki veya daha fazla etiket `<Endpoint` olur.

4. Etiketinin `<EndPoint>` içinde bir SomeService parametresi `name="`  `"` *(SomeService* bir uç nokta adını temsil eder) bulur. Bu, hizmet başvurusu için bir oluşturucu aşırı yüklemesi `endpointConfigurationName As String` geçirilen uç noktanın adıdır.

## <a name="how-to-call-a-service-method-asynchronously"></a>Nasıl yapılacak: Bir hizmet yöntemini zaman uyumsuz olarak çağırma

Communication Foundation (WCF) Windows çoğu yöntem zaman uyumlu veya zaman uyumsuz olarak çağrıl olabilir. Bir yöntemi zaman uyumsuz olarak çağırarak, yavaş bir bağlantı üzerinden çalışırken yöntemi çağrılırken, uygulamanın çalışmaya devam eder.

Varsayılan olarak, bir projeye bir hizmet başvurusu ekleniyorsa, yöntemleri zaman uyumlu olarak çağıran şekilde yapılandırılır. Hizmet Başvurularını Yapılandır iletişim kutusundaki bir ayarı değiştirerek yöntemleri zaman uyumsuz olarak çağırma **davranışını değiştirebilirsiniz.**

> [!NOTE]
> Bu seçenek hizmet başına temelinde ayarlanır. Bir hizmet için bir yöntem zaman uyumsuz olarak çağrılırsa, tüm yöntemlerin zaman uyumsuz olarak çağrılsı gerekir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Bir hizmet yöntemini zaman uyumsuz olarak çağırma

1. Bu **Çözüm Gezgini** hizmet başvurularını seçin.

2. Hizmet **Project** Hizmet Başvurularını **Yapılandır'a tıklayın.**

3. Hizmet **Başvurularını Yapılandır** iletişim kutusunda Zaman uyumsuz **işlemler oluştur onay kutusunu** seçin.

## <a name="how-to-bind-data-returned-by-a-service"></a>Nasıl kullanılır: Bir hizmet tarafından döndürülen verileri bağlama

Bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen verileri bir denetime diğer veri kaynaklarını bağlayabilirsiniz gibi bir denetime babilirsiniz. Bir WCF hizmetine başvuru eklerken, hizmet veri dönüş türü içeren bileşik türler içeriyorsa, bunlar otomatik olarak Veri Kaynakları **penceresine** eklenir.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WcF hizmeti tarafından döndürülen tek veri alanına denetim bağlamak için

1. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

   Veri **Kaynakları** penceresi görüntülenir.

2. Veri **Kaynakları penceresinde,** hizmet başvuru için düğümü genişletin. Hizmet ekranı tarafından döndürülen bileşik türler.

3. Bir tür için düğümü genişletin. Bu türe göre veri alanları görüntülenir.

4. Bir alan seçin ve açılan oka tıklar ve veri türü için kullanılabilir denetimlerin listesini görüntüler.

5. Bağlamak istediğiniz denetim türüne tıklayın.

6. Alanı bir forma sürükleyin. Denetim, bir bileşen ve bir bileşenle birlikte <xref:System.Windows.Forms.BindingSource> forma <xref:System.Windows.Forms.BindingNavigator> eklenir.

7. Bağlamak istediğiniz diğer alanlar için 4 ile 6 arasında adımları yineler.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WcF hizmeti tarafından döndürülen bileşik türe denetim bağlamak için

1. Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.** Veri **Kaynakları** penceresi görüntülenir.

2. Veri **Kaynakları penceresinde,** hizmet başvuru için düğümü genişletin. Hizmet ekranı tarafından döndürülen bileşik türler.

3. Bir tür için bir düğüm seçin ve kullanılabilir seçeneklerin listesini görüntülemek için açılan oka tıklayın.

4. Verileri bir **kılavuzda görüntülemek için DataGridView'a** veya verileri **tek tek denetimlerde** görüntülemek için Ayrıntılar'a tıklayın.

5. Düğümü forma sürükleyin. Denetimler, bir bileşen ve bir bileşenle <xref:System.Windows.Forms.BindingSource> birlikte forma <xref:System.Windows.Forms.BindingNavigator> eklenir.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Nasıl kullanılır: Bir hizmeti mevcut türleri yeniden kullanmak üzere yapılandırma

Bir projeye hizmet başvurusu ekleniyorsa, hizmette tanımlanan tüm türler yerel projede oluşturulur. Çoğu durumda, bir hizmet ortak .NET türleri kullandığında veya türler paylaşılan bir kitaplıkta tanımlandığı zaman yinelenen türler oluşturur.

Bu sorunu önlemek için, başvurulan derlemelerde türler varsayılan olarak paylaşılır. Bir veya daha fazla derleme için tür paylaşımını devre dışı bırakmak için Hizmet Başvurularını Yapılandır **iletişim kutusunda bunu** kullanabilirsiniz.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Tek bir derlemede tür paylaşımını devre dışı bırakmak için

1. Bu **Çözüm Gezgini** hizmet başvurularını seçin.

2. Hizmet **Project** Hizmet Başvurularını **Yapılandır'a tıklayın.**

3. Hizmet **Başvurularını Yapılandır iletişim kutusunda,** Belirtilen başvurulan **derlemelerde türleri yeniden kullan'ı seçin.**

4. Tür paylaşımını etkinleştirmek istediğiniz her derleme için onay kutusunu seçin. Derleme için tür paylaşımını devre dışı bırakmak için onay kutusunu boş bırakın.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Tüm derlemelerde tür paylaşımını devre dışı bırakmak için

1. Bu **Çözüm Gezgini** hizmet başvurularını seçin.

2. Hizmet **Project** Hizmet Başvurularını **Yapılandır'a tıklayın.**

3. Hizmet **Başvurularını Yapılandır iletişim kutusunda,** Başvurulan **derlemelerde türleri yeniden kullan onay** kutusunun işaretini kaldırın.

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Bu hizmetlerde WCF hizmetleri oluşturma ve kullanma hakkında adım adım bir Visual Studio. |
| [Adım adım kılavuz: WPF ve Entity Framework ile WCF veri hizmeti oluşturma](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Veri kaynaklarında veri oluşturma ve kullanma hakkında adım adım WCF Veri Hizmetleri bir Visual Studio. |
| [WCF geliştirme araçlarını kullanma](/dotnet/framework/wcf/using-the-wcf-development-tools) | Bu hizmetlerde WCF hizmetlerinin nasıl oluşturulacak ve test Visual Studio. |
| | [Nasıl kullanılır: WCF Veri Hizmeti başvurusu ekleme, güncelleştirme veya kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Hizmet başvurularını giderme](../data-tools/troubleshooting-service-references.md) | Hizmet başvurularına ve bunları önlemeye yönelik bazı yaygın hatalar sunar. |
| [WCF hizmetlerde hata ayıklama](../debugger/debugging-wcf-services.md) | WCF hizmetlerde hata ayıklarken karşılaş olabileceğiniz yaygın hata ayıklama sorunlarını ve tekniklerini açıklar. |
| [Adım adım kılavuz: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Türü belirli bir veri kümesi oluşturmak ve TableAdapter ile veri kümesi kodunu birden çok proje olarak ayırmak için adım adım yönergeler sağlar. |
| [Hizmet Başvurularını Yapılandır iletişim kutusu](../data-tools/configure-service-reference-dialog-box.md) | Hizmet Başvurularını Yapılandır iletişim kutusunun **kullanıcı arabirimi öğelerini** açıklar. |

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
