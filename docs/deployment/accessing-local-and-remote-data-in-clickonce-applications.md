---
title: Yerel & uzak veriye erişme (ClickOnce uygulamaları)
description: ClickOnce 'ın hem yerel olarak hem de uzaktan veri okuma ve yazma için verdiği çeşitli seçenekler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8bc59fd1d47a04b2f4c6ec2be9b9adb035f11e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837820"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>ClickOnce uygulamalarında yerel ve uzak veri erişimi
Çoğu uygulama veri kullanır veya üretir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , hem yerel olarak hem de uzaktan veri okumak ve yazmak için çeşitli seçenekler sunar.

## <a name="local-data"></a>Yerel Veriler
 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , aşağıdaki yöntemlerden herhangi birini kullanarak verileri yerel olarak yükleyebilir ve kaydedebilirsiniz:

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veri dizini

- Yalıtılmış Depolama

- Diğer yerel dosyalar

### <a name="clickonce-data-directory"></a>ClickOnce veri dizini
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Yerel bir bilgisayarda yüklü olan her uygulamanın, kullanıcının belgeler ve Ayarlar klasöründe depolanan bir veri dizini vardır. Bir uygulamaya eklenen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve "veri" dosyası olarak işaretlenen tüm dosyalar, bir uygulama yüklendiğinde bu dizine kopyalanır. Veri dosyaları, en sık kullanılan metin, XML ve Microsoft Access. mdb dosyaları gibi veritabanı dosyaları olan herhangi bir dosya türünde olabilir.

 Veri dizini, uygulamanın açıkça sakladığı ve sakladığı veriler olan uygulama tarafından yönetilen verilere yöneliktir. Uygulama bildiriminde "veri" olarak işaretlenmemiş tüm statik, bağımlılığı olmayan dosyalar, uygulama dizininde yer alır. Bu dizin, uygulamanın yürütülebilir (*. exe*) dosyalarının ve derlemelerinin bulunduğu yerdir.

> [!NOTE]
> Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama kaldırıldığında, veri dizini de kaldırılır. Veri dizinini, belgeler gibi son kullanıcı tarafından yönetilen verileri depolamak için hiçbir şekilde kullanmayın.

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>ClickOnce dağıtımındaki veri dosyalarını işaretleme
 Var olan bir dosyayı veri dizinine koymak için, mevcut dosyayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızın uygulama bildirimi dosyasında bir veri dosyası olarak işaretlemeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

#### <a name="read-from-and-write-to-the-data-directory"></a>Veri dizininden okuma ve yazma
 Veri dizininden okuma, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızın okuma izni istemesini gerektirir; benzer şekilde, dizine yazmak Için yazma izni gerekir. Uygulamanız tam güvenle çalışacak şekilde yapılandırıldıysa bu izne otomatik olarak sahip olur. Izin yükseltmesini veya güvenilir uygulama dağıtımını kullanarak uygulamanıza ilişkin izinleri yükseltme hakkında daha fazla bilgi için bkz. [güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Kuruluşunuz güvenilir uygulama dağıtımı kullanmıyorsa ve Izin yükseltmesini devre dışı bırakırsanız, izinler başarısız olur.

 Uygulamanız bu izinlere sahip olduktan sonra, içindeki sınıflarda yöntem çağrılarını kullanarak veri dizinine erişebilir <xref:System.IO> . Veri dizininin yolunu, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> öğesinin özelliğinde tanımlanan özelliğini kullanarak bir Windows Forms uygulaması içinde elde edebilirsiniz <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> <xref:System.Deployment.Application.ApplicationDeployment> . Verilerinize erişmek için en kullanışlı ve önerilen yöntem budur. Aşağıdaki kod örneği, bir veri dosyası olarak dağıtımınıza eklediğiniz *CSV.txt* adlı bir metin dosyası için nasıl yapılacağını gösterir.

 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]

 Dağıtımınızdaki dosyaları veri dosyası olarak işaretleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir ClickOnce uygulamasına veri dosyası ekleme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

 Ayrıca, sınıfında, gibi ilgili değişkenleri kullanarak veri dizini yolunu elde edebilirsiniz <xref:System.Windows.Forms.Application> <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A> .

 Diğer dosya türlerini işlemek için ek izinler gerekebilir. Örneğin, bir Access Database (*. mdb*) dosyası kullanmak istiyorsanız, uygulamanızın ilgili sınıfları kullanabilmesi için tam güven onayı gerekir \<xref:System.Data> .

#### <a name="data-directory-and-application-versions"></a>Veri dizini ve uygulama sürümleri
 Bir uygulamanın her sürümü kendi veri dizinine sahiptir ve bu, diğer sürümlerden yalıtılmıştır. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın çalışma zamanında yeni veri dosyaları oluşturmak için bir konumu olması adına, dağıtıma dahil edilmiş herhangi bir veri dosyası olup olmadığından bağımsız olarak bu dizini oluşturur. Bir uygulamanın yeni bir sürümü yüklendiğinde, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önceki sürümün veri dizinindeki tüm mevcut veri dosyalarını, özgün dağıtıma dahil edilip edilmeyeceğini veya uygulama tarafından oluşturulup oluşturulmayacağını yeni sürümün veri dizinine kopyalayacaktır.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bir veri dosyasının yeni sürümde uygulamanın eski sürümünde farklı bir karma değeri varsa, dosyanın eski sürümünü sunucunun yeni sürümüyle değiştirir. Ayrıca, uygulamanın önceki sürümü yeni sürümün dağıtımına dahil olan bir dosyayla aynı ada sahip yeni bir dosya oluşturulduysa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eski sürümün dosyasının üzerine yeni dosya yazılır. Her iki durumda da eski dosyalar, adlı veri dizini içindeki bir alt dizine dahil edilir `.pre` , böylece uygulama geçiş amacıyla eski verilere erişmeye devam edebilir.

 Verilerin daha ayrıntılı geçirilmesi gerekiyorsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eski veri dizininden yeni veri dizinine özel geçiş yapmak için DAĞıTıM API 'sini kullanabilirsiniz. Kullanarak kullanılabilir bir indirmeyi test etmeniz <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A> , veya kullanarak güncelleştirmeyi indirmeniz <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A> ve güncelleştirme tamamlandıktan sonra herhangi bir özel veri geçişi çalışmasını yapmanız gerekir.

### <a name="isolated-storage"></a>Yalıtılmış depolama
 Yalıtılmış depolama, basit bir API kullanarak dosya oluşturmak ve bunlara erişmek için bir API sağlar. Depolanan dosyaların gerçek konumu hem geliştiriciden hem de kullanıcıdan gizlenir.

 Yalıtılmış depolama .NET Framework tüm sürümlerinde çalışmaktadır. Yalıtılmış depolama, ek izin onayları gerekmeden kısmen güvenilen uygulamalarda da kullanılabilir. Uygulamanızın kısmi güvende çalışması gerekiyorsa, ancak uygulamaya özgü verileri korumalıdır, yalıtılmış depolamayı kullanmanız gerekir.

 Daha fazla bilgi için bkz. [yalıtılmış depolama](/dotnet/standard/io/isolated-storage).

### <a name="other-local-files"></a>Diğer yerel dosyalar
 Uygulamanızın rapor, görüntü, müzik ve benzeri Son Kullanıcı verilerini ile çalışması veya kaydetmesi gerekiyorsa, uygulamanızın <xref:System.Security.Permissions.FileIOPermission> yerel dosya sistemine veri okuması ve yazması gerekir.

## <a name="remote-data"></a>Uzak veriler
 Bazı bir noktada, uygulamanız büyük olasılıkla müşteri verileri veya Pazar bilgileri gibi uzak bir Web sitesinden bilgi almak zorunda kalır. Bu bölümde, uzak verileri almak için en yaygın teknikler açıklanmaktadır.

### <a name="access-files-with-http"></a>HTTP ile dosyalara erişme
 Bir Web sunucusundan, <xref:System.Net.WebClient> ya da <xref:System.Net.HttpWebRequest> ad alanındaki sınıfını kullanarak verilere erişebilirsiniz <xref:System.Net> . Veriler, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ham metin veya XML verileri döndüren statik dosyalar ya da uygulamalar olabilir. Verileriniz XML biçimindeyse, verileri almanın en hızlı yolu, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Load%2A> yöntemi bağımsız değişken olarak bir URL 'yi alan sınıfını kullanmaktır. Bir örnek için bkz. [Dom 'DA XML belgesi okuma](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).

 Uygulamanız HTTP üzerinden uzak verilere eriştiğinde güvenliği göz önünde bulundurmanız gerekir. Varsayılan olarak uygulamanızın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ağ kaynaklarına erişimi, uygulamanızın nasıl dağıtıldığına bağlı olarak kısıtlanmış olabilir. Bu kısıtlamalar, kötü amaçlı programların ayrıcalıklı uzak verilere erişim sağlamasını veya ağdaki diğer bilgisayarlara saldırmak için bir kullanıcının bilgisayarını kullanmasını önlemeye yönelik olarak uygulanır.

 Aşağıdaki tabloda, kullanabileceğiniz dağıtım stratejileri ve bunların varsayılan Web izinleri listelenmektedir.

|Dağıtım türü|Varsayılan ağ izinleri|
|---------------------|---------------------------------|
|Web yüklemesi|Yalnızca uygulamanın yüklendiği Web sunucusuna erişebilir|
|Dosya paylaşımının yüklenmesi|Hiçbir Web sunucusuna erişilemiyor|
|CD-ROM yüklemesi|Herhangi bir Web sunucusuna erişebilir|

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanız güvenlik kısıtlamaları nedeniyle bir Web sunucusuna erişemediği takdirde uygulamanın <xref:System.Net.WebPermission> Bu web sitesi için onay olması gerekir. Bir uygulama için güvenlik izinlerini artırma hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bkz. [güvenli ClickOnce uygulamaları](../deployment/securing-clickonce-applications.md).

### <a name="access-data-through-an-xml-web-service"></a>XML Web hizmeti üzerinden verilere erişme
 Verilerinizi bir XML Web hizmeti olarak kullanıma sundıysanız, verilere bir XML Web hizmeti proxy 'si kullanarak erişebilirsiniz. Proxy, kullanarak oluşturduğunuz bir .NET Framework sınıfıdır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . XML Web hizmeti 'nin (örneğin, müşterileri alma, sipariş yerleştirme vb.) işlemleri proxy üzerinde yöntemler olarak gösterilir. Bu, Web hizmetlerinin ham metin veya XML dosyalarından kullanımını çok daha kolay hale getirir.

 XML Web hizmetiniz HTTP üzerinden çalışıyorsa, hizmet ve sınıflarıyla aynı güvenlik kısıtlamalarına göre bağlanır <xref:System.Net.WebClient> <xref:System.Net.HttpWebRequest> .

### <a name="access-a-database-directly"></a>Veritabanına doğrudan erişme
 <xref:System.Data>Ağınızdaki SQL Server gibi bir veritabanı sunucusuyla doğrudan bağlantı kurmak için ad alanı içindeki sınıfları kullanabilirsiniz, ancak güvenlik sorunlarını dikkate almalısınız. HTTP isteklerinden farklı olarak, veritabanı bağlantı istekleri kısmi güven altında her zaman varsayılan olarak yasaktır; yalnızca [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızı BIR CD-ROM ' d a n yüklerseniz varsayılan olarak bu izinlere sahip olursunuz. Bu, uygulamanıza tam güven sağlar. Belirli bir SQL Server veritabanına erişimi etkinleştirmek için uygulamanızın buna istemesi gerekir <xref:System.Data.SqlClient.SqlClientPermission> ; SQL Server dışında bir veritabanına erişimi etkinleştirmek için, istemesi gerekir <xref:System.Data.OleDb.OleDbPermission> .

 Çoğu zaman, veritabanına doğrudan erişmeniz gerekmez, ancak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] veya BIR XML Web hizmetinde yazılmış bir Web sunucusu uygulaması aracılığıyla bunun yerine ona erişir. Bu şekilde veritabanına erişmek, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanız bir Web sunucusundan dağıtılırsa en iyi yöntemdir. Uygulamanızın izinlerini yükseltme yapmadan kısmi güvende sunucuya erişebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil etme](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)