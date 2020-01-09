---
title: Windows Communication Foundation ve WCF Veri Hizmetleri
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: abcfde777223ada130e06ab7766319e1d982258c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585944"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri

Visual Studio, dağıtılmış uygulamalar oluşturmaya yönelik Windows Communication Foundation (WCF) ve WCF Veri Hizmetleri, Microsoft teknolojileri ile çalışmaya yönelik araçlar sağlar. Bu konu, Visual Studio perspektifinden hizmetlere giriş sağlar. Tüm belgeler için bkz. [WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>WCF nedir?

Windows Communication Foundation (WCF), güvenli, güvenilir, işlem temelli ve birlikte çalışabilen dağıtılmış uygulamalar oluşturmaya yönelik Birleşik bir çerçevedir. ASMX Web Hizmetleri, .NET Remoting, Enterprise Services (DCOM) ve MSMQ gibi eski işlemler arası iletişim teknolojilerinin yerini alır. WCF bu teknolojilerden birleşik bir programlama modeli altında işlevselliğini bir araya getirir. Bu, dağıtılmış uygulamalar geliştirme deneyimi basitleştirir.

### <a name="what-are-wcf-data-services"></a>WCF Veri Hizmetleri nelerdir

WCF Veri Hizmetleri, açık veri (OData) protokolü standardının bir uygulamasıdır.  WCF Veri Hizmetleri, tablo verilerini bir dizi REST API 'si olarak kullanıma sunmanızı sağlayarak GET, POST, PUT veya DELETE gibi standart HTTP fiillerini kullanarak veri döndürmenize olanak tanır. Sunucu tarafında, WCF Veri Hizmetleri tarafından değiştirilen [ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis) yeni OData hizmetlerini oluşturma. WCF Veri Hizmetleri istemci kitaplığı, Visual Studio 'dan bir .NET uygulamasında (**proje** > **hizmet başvurusu Ekle**) OData hizmetlerini kullanmak için iyi bir seçenek olmaya devam etmektedir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>WCF programlama modeli

WCF programlama modeli iki varlık arasındaki iletişimi temel alır: bir WCF hizmeti ve WCF istemcisi. Programlama modeli, .NET 'teki <xref:System.ServiceModel> ad alanında kapsüllenir.

### <a name="wcf-service"></a>WCF Hizmeti

Bir WCF hizmeti, hizmet ve istemci arasındaki bir sözleşme tanımlayan bir arabirim dayanır. İle işaretlenmiş bir <xref:System.ServiceModel.ServiceContractAttribute> aşağıdaki kodda gösterildiği gibi öznitelik:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

İşlevleri veya yöntemleri ile işaretleyerek bir WCF hizmeti tarafından sunulan tanımladığınız bir <xref:System.ServiceModel.OperationContractAttribute> özniteliği.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Ayrıca, bileşik bir türü ile işaretleyerek serileştirilmiş verilerini açığa çıkarabilir bir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. Bu, istemcisinde veri bağlama sağlar.

Bir arabirim ve metotlarını tanımlandıktan sonra bunlar arabirimi uygulayan bir sınıf içinde kapsüllenir. Tek bir WCF hizmet sınıfı, birden çok hizmet sözleşmelerini uygulayabilirsiniz.

Bir WCF hizmeti olarak tüketim üzerinden ne bilinen için sunulan bir *uç nokta*. Uç nokta hizmetiyle iletişim kurmak için tek yolu sağlar. diğer sınıflarla gibi bir doğrudan başvuru hizmetine erişilemiyor.

Bir uç nokta, adres, bağlama ve bir sözleşme oluşur. Hizmet bulunduğu adresi tanımlar; Bu URL, bir FTP adresi veya ağ ya da yerel yolu olabilir. Bir bağlama hizmeti ile iletişim bir şekilde tanımlar. WCF bağlamaları, HTTP veya FTP, Windows kimlik doğrulaması veya kullanıcı adları ve parolalar gibi bir güvenlik mekanizması gibi bir protokol belirtmek için verimli bir model sağlar ve daha fazlasını. Bir sözleşme WCF hizmet sınıfı tarafından sunulan işlemlerini içerir.

Birden fazla uç nokta için tek bir WCF hizmet sunulabilir. Bu, farklı şekilde aynı hizmetle iletişim kurmak farklı istemcilerin sağlar. Örneğin, bir bankacılık hizmeti bir uç nokta çalışanlar ve başka bir dış müşteriler için her bağlama, farklı bir adres kullanarak sağlar ve/veya sözleşme.

### <a name="wcf-client"></a>WCF istemcisi

Bir WCF istemcisi oluşan bir *proxy* bir WCF Hizmeti ile iletişim kurmak bir uygulama sağlar ve bir uç nokta eşleşen bir uç nokta için hizmet tanımlı. Proxy, *app. config* dosyasındaki istemci tarafında oluşturulur ve hizmet tarafından açığa çıkarılan türler ve yöntemler hakkında bilgi içerir. Birden çok uç noktalarını kullanıma Hizmetleri için istemci kendi gereksinimlerini, örneğin, HTTP üzerinden iletişim kurmak ve Windows kimlik doğrulaması kullanmak için en uygun olanı seçebilirsiniz.

Bir WCF istemcisi oluşturulduktan sonra diğer nesnelerde olduğu gibi kodunuzda hizmete başvuramaz. Örneğin, çağrılacak `GetData` yazma aşağıdakine benzer kod daha önce gösterilen yöntemi:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 'da WCF araçları

Visual Studio, WCF Hizmetleri ve WCF istemcileri oluşturmanıza yardımcı olacak araçlar sağlar. Araçları gösteren bir izlenecek yol için, bkz. [Izlenecek yol: Windows Forms basit BIR WCF hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>WCF Hizmetleri oluşturma ve test etme

Kendi hizmetinizi hızlı bir şekilde oluşturmak için WCF Visual Studio şablonlarını bir temel olarak kullanabilirsiniz. Ardından, hata ayıklamak ve hizmeti test etmek için WCF hizmet otomatik konağı ve WCF Test İstemcisi kullanabilirsiniz. Bu araçlar birlikte hızlı ve kolay bir hata ayıklama ve test döngüsünü sağlamak ve erken bir aşamada bir barındırma modeli için işleme gereksinimini ortadan kaldırır.

#### <a name="wcf-templates"></a>WCF şablonları

WCF Visual Studio şablonları, hizmet geliştirme için temel bir sınıf yapısı sağlar. WCF çeşitli şablonlar kullanılabilir **Yeni Proje Ekle** iletişim kutusu. Bunlar WCF hizmeti lLibrary projelerini, WCF hizmeti Web sitelerini ve WCF hizmeti öğe şablonlarını içerir.

Bir şablon seçin, bir hizmet sözleşmesi, hizmet uygulaması ve hizmet yapılandırması için dosyalar eklenir. Hizmet, basit bir "Merhaba Dünya" türünü oluşturma, tüm gerekli özniteliklere zaten eklenir ve kod yazmadan yoktu. Elbette, işlevleri ve gerçek dünya hizmetiniz için yöntemler sağlamak üzere kod eklemek istediğiniz ancak şablonların temel sağlamasıdır.

WCF şablonları hakkında daha fazla bilgi için bkz. [WCF Visual Studio şablonları](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>WCF hizmet ana bilgisayarı

Bir WCF hizmeti projesi için Visual Studio hata ayıklayıcısını başlattığınızda ( **F5**tuşuna basarak), hizmeti yerel olarak BARıNDıRMAK Için WCF hizmeti ana bilgisayar aracı otomatik olarak başlatılır. WCF hizmeti ana bilgisayarı bir WCF hizmeti projesindeki Hizmetleri numaralandırır, projenin yapılandırmasını yükler ve bulduğu her hizmet için bir konak başlatır.

WCF hizmet konağı kullanarak ek kod yazmadan veya belirli bir ana bilgisayara geliştirme sırasında yürüten olmadan bir WCF Hizmeti sınayabilirsiniz.

WCF hizmet ana bilgisayarı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost. exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>WCF Test istemcisi

WCF Test İstemcisi aracı test parametreleri giriş, bir WCF hizmeti için girdi gönderme sağlar ve hizmet geri gönderir yanıtı görüntüleyin. Bu deneyimi ile WCF hizmet konağı birleştirdiğinizde test uygun bir hizmet sağlar. Aracı *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* klasöründe bulun.

WCF hizmeti projesinde hata ayıklamak için **F5** tuşuna BASTıĞıNıZDA, WCF Test istemcisi açılır ve yapılandırma dosyasında tanımlanan hizmet uç noktalarının bir listesini görüntüler. Test parametreleri ve hizmeti başlatın ve sürekli olarak test edin ve hizmetinizi doğrulamak için bu işlemi yineleyin.

WCF test Istemcisi hakkında daha fazla bilgi edinmek için bkz. [WCF Test istemcisi (WcfTestClient. exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio 'da WCF hizmetlerine erişme

Visual Studio, WCF istemcileri oluşturma görevini basitleştirir, otomatik olarak bir ara sunucu ve **hizmet başvurusu Ekle** iletişim kutusunu kullanarak eklediğiniz hizmetler için bir uç nokta oluşturur. Tüm gerekli yapılandırma bilgileri *app. config* dosyasına eklenir. Çoğu zaman tüm yapmanız gereken olan örneği hizmet kullanmak için.

**Hizmet Başvurusu Ekle** iletişim kutusu için bir hizmet adresini girin ya da çözümünüz içinde tanımlanan bir hizmet için aranacak sağlar. İletişim kutusu, hizmetleri ve bu hizmetlerin sunduğu işlemleri listesini döndürür. Ayrıca kod Hizmetleri'nde başvurur ad alanı tanımlamanıza olanak sağlar.

**Yapılandırma hizmet başvuruları** iletişim kutusu, hizmet yapılandırmasını özelleştirmenizi sağlar. Hizmet adresini değiştirmek, erişim düzeyi, zaman uyumsuz davranış ve ileti anlaşması türleri belirtin ve tür yeniden yapılandırın.

## <a name="how-to-select-a-service-endpoint"></a>Nasıl yapılır: hizmet uç noktası seçme

Bazı Windows Communication Foundation (WCF) Hizmetleri bir istemci hizmeti ile iletişim kurabilir birden çok uç noktalarını kullanıma sunar. Örneğin, bir hizmet, bir HTTP bağlaması ve Kullanıcı adı ve parola güvenliği kullanan bir uç nokta ve FTP ve Windows kimlik doğrulaması kullanan ikinci bir uç nokta açığa çıkabilir. İkinci bir intranet üzerinde kullanılabilir ise ilk uç hizmeti bir güvenlik duvarı dışından erişen uygulamalar tarafından kullanılıyor olabilir.

Böyle bir durumda, belirttiğiniz `endpointConfigurationName` bir parametresi olarak bir hizmet başvurusu için oluşturucu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Hizmet uç noktası seçin

1. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **hizmet başvurusu Ekle**' yi seçerek bir WCF hizmetine bir başvuru ekleyin.

2. Kod Düzenleyicisi'nde hizmet başvurusu için bir oluşturucu ekleyin:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Değiştirin *ServiceReference* değiştirin ve hizmet başvurusu için ad alanı ile *Service1Client* hizmetin adı.

3. Oluşturucunun aşırı yüklerini içeren bir IntelliSense listesi görüntülenir. Seçin `endpointConfigurationName As String` aşırı yükleme.

4. Aşırı yükleme yazın `=` *ConfigurationName*burada *ConfigurationName* kullanmak istediğiniz uç noktaya adıdır.

    > [!NOTE]
    > Kullanılabilir uç noktaların adlarını bilinmediğinizde, bunları *app. config* dosyasında bulabilirsiniz.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Bir WCF hizmeti için kullanılabilir uç noktalar bulmak için

1. **Çözüm Gezgini**' de, hizmet başvurusunu içeren proje için **app. config** dosyasına sağ tıklayın ve sonra **Aç**' a tıklayın. Dosya kod düzenleyicisinde görünür.

2. Arama `<Client>` dosyasındaki etiketi.

3. Altındaki arama `<Client>` etiketi ile başlayan etiket `<Endpoint>`.

     Hizmet başvurusu birden fazla uç nokta sağlıyorsa, olacaktır iki veya daha fazla `<Endpoint` etiketler.

4. `<EndPoint>` etiketinin içinde, bir `name="`*someservice*`"` parametresi ( *SomeService* 'in bir uç nokta adını temsil ettiği) bulacaksınız. Geçirilebilir uç nokta unvanıdır `endpointConfigurationName As String` bir hizmet başvurusu için bir oluşturucu aşırı yüklemesi.

## <a name="how-to-call-a-service-method-asynchronously"></a>Nasıl yapılır: bir hizmet yöntemini zaman uyumsuz olarak çağırma

Windows Communication Foundation (WCF) hizmetlerini çoğu yöntemleri zaman uyumlu veya zaman uyumsuz olarak çağrılabilir. Zaman uyumsuz bir yöntemi çağırmak uygulamanızın yavaş bir bağlantı üzerinden çalıştığında yöntemi Aranan çalışmaya devam olanak tanır.

Varsayılan olarak, bir projeye bir hizmet başvurusu eklendiğinde, yöntemleri zaman uyumlu olarak çağırmak üzere yapılandırılır. Bir ayarı değiştirerek zaman uyumsuz yöntemleri çağırma davranışını değiştirebilirsiniz **hizmet başvurusu yapılandırma** iletişim kutusu.

> [!NOTE]
> Bu seçenek, bir hizmet başına temelinde ayarlanır. Zaman uyumsuz olarak bir hizmet için bir yöntem çağrılırsa, tüm yöntemlerin zaman uyumsuz olarak çağrılmalıdır.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Bir hizmet yöntemini zaman uyumsuz olarak çağırma

1. İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2. Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3. İçinde **hizmet başvurusu yapılandırma** iletişim kutusunda **zaman uyumsuz işlemler oluşturma** onay kutusu.

## <a name="how-to-bind-data-returned-by-a-service"></a>Nasıl yapılır: bir hizmet tarafından döndürülen verileri bağlama

Yalnızca bir denetim için herhangi bir veri kaynağını bağlayabilirsiniz gibi bir denetim için bir Windows Communication Foundation (WCF) hizmeti tarafından döndürülen veriler bağlayabilirsiniz. Hizmet veri döndüren bileşik türler içeriyorsa bir WCF hizmeti bir başvuru eklediğinizde, otomatik olarak eklenen **veri kaynakları** penceresi.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen tek bir veri alanı denetim Bağlanılacak

1. Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi görüntülenir.

2. İçinde **veri kaynakları** penceresinde, hizmet başvurusu düğümünü genişletin. Hizmet görüntüsü tarafından döndürülen bileşik türler.

3. Bir tür için bir düğümünü genişletin. Bu tür için veri alanları görüntülenir.

4. Bir alan seçin ve veri türü için uygun olan denetimler listesini görüntülemek için açılan oka tıklayın.

5. Bağlamak istediğiniz denetim türüne tıklayın.

6. Alanı form üzerine sürükleyin. Denetim, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeniyle birlikte forma eklenir.

7. 6 herhangi diğer alanları ancak 4 arasındaki adımları yineleyin bağlamak istediğiniz.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Bir WCF hizmeti tarafından döndürülen bileşik türü bir denetim Bağlanılacak

1. Üzerinde **veri** menüsünde **veri kaynaklarını Göster**. **Veri kaynakları** penceresi görüntülenir.

2. İçinde **veri kaynakları** penceresinde, hizmet başvurusu düğümünü genişletin. Hizmet görüntüsü tarafından döndürülen bileşik türler.

3. Bir tür için bir düğüm seçin ve kullanılabilir seçeneklerin bir listesini görüntülemek için açılan oka tıklayın.

4. Tıklayın **DataGridView** veri kılavuzunda görüntülemek için veya **ayrıntıları** bireysel denetimlerinde verileri görüntülemek için.

5. Düğümü form üzerine sürükleyin. Denetimler, bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bir <xref:System.Windows.Forms.BindingNavigator> bileşeniyle birlikte forma eklenir.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Nasıl yapılır: mevcut türleri yeniden kullanmak için bir hizmet yapılandırma

Bir hizmet başvurusu için bir proje eklendiğinde, hizmette tanımlanan herhangi bir türü yerel projede oluşturulur. Çoğu durumda bu, bir hizmet ortak .NET türlerini kullandığında veya türler paylaşılan bir kitaplıkta tanımlandığında yinelenen türler oluşturur.

Bu sorunu önlemek için bütünleştirilmiş kodlardaki türleri varsayılan olarak paylaşılır. Tür için bir veya daha fazla derlemeleri paylaşımı devre dışı bırakmak isterseniz, bu nedenle, bunu yapabilirsiniz **yapılandırma hizmet başvuruları** iletişim kutusu.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Tek bir bütünleştirilmiş kod paylaşımı türü devre dışı bırakmak için

1. İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2. Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3. İçinde **yapılandırma hizmet başvuruları** iletişim kutusunda **belirtilen bütünleştirilmiş kodlardaki türleri yeniden**.

4. Tür paylaşımını etkinleştirmek istediğiniz her derleme için onay kutusunu seçin. Bir derleme için paylaşım türü devre dışı bırakmak için onay kutusunu temizleyin.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Tüm derlemelerde paylaşım türü devre dışı bırakmak için

1. İçinde **Çözüm Gezgini**, hizmet başvurusunu seçin.

2. Üzerinde **proje** menüsünü tıklatın **hizmet başvurusu Yapılandır**.

3. İçinde **yapılandırma hizmet başvuruları** iletişim kutusu, NET **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu.

## <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Visual Studio 'da WCF Hizmetleri oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar. |
| [İzlenecek yol: WPF ve Entity Framework bir WCF veri hizmeti oluşturma](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Visual Studio 'da WCF Veri Hizmetleri oluşturma ve kullanma hakkında adım adım bir tanıtım sağlar. |
| [WCF geliştirme araçlarını kullanma](/dotnet/framework/wcf/using-the-wcf-development-tools) | Visual Studio 'da WCF hizmetlerinin nasıl oluşturulduğunu ve test yapıldığını açıklar. |
| | [Nasıl yapılır: WCF veri hizmeti başvurusu ekleme, güncelleştirme veya kaldırma](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Hizmet başvurularının sorunlarını giderme](../data-tools/troubleshooting-service-references.md) | Hizmet başvuruları ve bunların nasıl ile ortaya çıkabilecek bazı yaygın hatalar gösterir. |
| [WCF hizmetlerinde hata ayıklama](../debugger/debugging-wcf-services.md) | Genel hata ayıklama sorunları ve WCF hizmetlerinde hata ayıklama sırasında karşılaşabileceğiniz teknikleri açıklar. |
| [İzlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Türü belirtilmiş veri kümesi oluşturma ve birden çok projelere TableAdapter ve veri kümesi kodunu ayırmak için adım adım yönergeler sağlar. |
| [Hizmet başvurusunu yapılandırma iletişim kutusu](../data-tools/configure-service-reference-dialog-box.md) | Kullanıcı arabirimi öğelerini açıklar **hizmet başvurusu yapılandırma** iletişim kutusu. |

## <a name="reference"></a>Başvuru

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
