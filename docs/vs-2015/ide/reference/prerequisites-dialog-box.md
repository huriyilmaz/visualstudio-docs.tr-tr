---
title: Önkoşullar Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbd3e348aa4495a897e57ec46d16273a46dccdf1
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851679"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, hangi önkoşul bileşenlerinin yüklendiğini, bunların nasıl yüklendiğini ve paketlerin hangi sırayla yüklendiğini belirtir.

 Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Yayımla** sekmesine tıklayın. **Yayımla** sayfasında, **Önkoşullar**' ı tıklatın. Kurulum projeleri için, **Proje** menüsünde **Özellikler**' e tıklayın. **Özellik sayfaları** iletişim kutusu göründüğünde, **Önkoşullar**' ı tıklatın.

## <a name="uielement-list"></a>UIElement Listesi

|Öğe|Açıklama|
|-------------|-----------------|
|**Önkoşul bileşenlerini yüklemek için Kurulum programı oluşturma**|Uygulamanızın uygulama Kurulum programında (Setup. exe) Önkoşul bileşenlerini, bağımlılık sırasına göre uygulamanızın önüne yüklenebilmeleri için içerir. Varsayılan olarak, bu seçenek seçilidir. Seçili değilse, Setup. exe oluşturulmaz.|
|**Hangi önkoşulların yükleneceğini seçin**|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports vb. gibi bileşenlerin yüklenip yüklenmeyeceğini belirtir.<br /><br /> Örneğin, **SQL Server 2005 Express sürüm SP2**' nin yanındaki onay kutusunu seçerek, Kurulum programının bu bileşenin hedef bilgisayarda yüklü olup olmadığını doğrulaması gerektiğini ve daha önce yüklenmemişse yüklemeyi belirtirsiniz.<br /><br /> Her önkoşul paketiyle ilgili ayrıntılı bilgi için, bu konunun ilerleyen kısımlarında önkoşul bilgileri tablosuna bakın.|
|**Daha yeniden dağıtılabilir bileşenler için Microsoft Update işaretleyin**|Bu bağlantıya tıkladığınızda, güncelleştirmeleri denetlemek için bileşenler Web sitesini yeniden [dağıtmak üzere önyükleyici paketlerine](https://msdn.microsoft.com/vstudio/bb898654.aspx) gidersiniz.|
|**Önkoşulları bileşen satıcısının Web sitesinden indir**|Önkoşul bileşenlerinin satıcının Web sitesinden yükleneceğini belirtir. Bu varsayılan seçenektir.|
|**Önkoşulları Uygulamam ile aynı konumdan indir**|Önkoşul bileşenlerinin uygulamayla aynı konumdan yükleneceğini belirtir. Bu, tüm önkoşul paketlerini yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
|**Önkoşulları aşağıdaki konumdan indirin**|Önkoşul bileşenlerinin seçtiğiniz konumdan yükleneceğini belirtir. Bir konum seçmek için, **tarayıcı** düğmesini kullanabilirsiniz.|

## <a name="prerequisites-information"></a>Önkoşul bilgileri
 **Önkoşullar** iletişim kutusunda görünen önkoşul bileşenleri, aşağıdaki listede yer alan uygulamalardan farklı görünebilir. **Önkoşullar Iletişim kutusunda** listelenen önkoşul paketleri, iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile seçmeniz gerekir.

|Öğe|Açıklama|
|-------------|-----------------|
|**.NET Framework 3,5 SP1**|Bu paket aşağıdakileri yükleyerek:<br /><br /> -2,0, 3,0 ve 3,5 sürümlerini .NET Framework.<br />-32-bit (x86) ve 64 bit (x64) işletim sistemlerindeki tüm .NET Framework sürümleri için destek.<br />-Paketiyle birlikte yüklenen her bir .NET Framework sürümü için dil paketleri.<br />-.NET Framework 2,0 ve 3,0 için hizmet paketleri.<br /><br /> .NET Framework 3,0, Windows Vista 'da bulunur ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].NET Framework 3,5 eklenmiştir. .NET Framework 3,5, 32 bit işletim sistemleri için derlenen C# ve hedef Framework 'ün **.NET Framework 3,5**olarak ayarlandığı ve 64-bit işletim sistemleri Için derlenen Visual Basic ve görsel C# projelerde bir bütün Visual Basic ve Visual projeleri için gereklidir. (IA64 desteklenmez.) Visual Basic ve görsel C# projelerin varsayılan olarak HERHANGI bir CPU mimarisi için derlendiğini unutmayın. Daha fazla bilgi için bkz. [Visual Studio multi-hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md), [.NET Framework yeniden dağıtma](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287)ve [64 bitlik uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Varsayılan olarak, bu öğe seçilidir.|
|**.NET Framework 3,5 SP1 Istemci profili**|.NET Framework Istemci profili, istemci uygulamaları hedefleyen tam .NET Framework 3,5 SP1'IN bir alt kümesidir. Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) ve ClickOnce özelliklerinin kolaylaştırılmış bir alt kümesini sağlar. Bu, .NET Framework Istemci profilini hedefleyen WPF, Windows Forms, WCF ve konsol uygulamaları için hızlı dağıtım senaryolarına izin vermez. Daha fazla bilgi için bkz. [.NET Framework Istemci profili](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|
|**Microsoft .NET Framework 4 (x86 ve x64)**|Bu paket, hem x86 hem de x64 platformları için .NET Framework 4 ' ü yükleme.<br /><br /> Daha fazla bilgi için bkz. [Visual Studio multi-hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md), [.NET Framework yeniden dağıtma](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287)ve [64 bitlik uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Varsayılan olarak, bu öğe seçilidir.|
|**Microsoft .NET Framework 4 Istemci profili (x86 ve x64)**|.NET Framework 4 Istemci profili, istemci uygulamaları hedefleyen tam .NET Framework 4 ' ün bir alt kümesidir. Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) ve ClickOnce özelliklerinin kolaylaştırılmış bir alt kümesini sağlar. Bu, .NET Framework 4 Istemci profilini hedefleyen WPF, Windows Forms ve konsol uygulamaları için hızlı dağıtım senaryolarına izin vermez. Daha fazla bilgi için bkz. [.NET Framework Istemci profili](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|
|**Microsoft Office 2007 birincil birlikte çalışma derlemeleri**|Bu paket, 2007 Microsoft Office ürünleri için birincil birlikte çalışma derlemelerini yükleme. Birincil birlikte çalışma derlemesi, yönetilen kodun bir Microsoft Office uygulamasının COM tabanlı nesne modeliyle etkileşime geçmesini sağlar. Daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|
|**Microsoft Visual Basic PowerPacks sürüm 10,0**|Power Packs, Visual Basic uygulamalar geliştirmeye yardımcı olacak Eklentiler, denetimler, bileşenler ve araçlardır. Bu sürüm, bir Windows formunun içeriğini yazdırmanızı sağlayan [PrintForm](/previous-versions/bb882742(v=vs.140)) bileşenini ve Visual Basic 6,0 Yazıcı kodunun değiştirilmemiş olarak çalışmasını sağlayan yazıcı uyumluluk kitaplığını içerir.|
|**.NET 2,0 F# Için Microsoft Visual Runtime**|Bu paket, işlev programlama F# ve geleneksel nesne yönelimli ve kesinlik (yordamsal) programlama için destek sağlayan x86 ve x64 işletim sistemlerine yönelik görsel çalışma zamanı kitaplıklarını yüklemektedir. Uygulama veya bileşenleri Visual F# 'te yazılmışsa ve 2,0, .NET Framework 3,0 veya .NET Framework 3,5 .NET Framework bu paketin yüklenmesi gerekir.<br /><br /> Daha fazla bilgi için bkz [ F# . dil başvurusu](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|
|**.NET 4,0 F# Için Microsoft Visual Runtime**|Bu paket, işlev programlama F# ve geleneksel nesne yönelimli ve kesinlik (yordamsal) programlama için destek sağlayan x86 ve x64 işletim sistemlerine yönelik görsel çalışma zamanı kitaplıklarını yüklemektedir. Uygulama veya bileşenleri Visual F# ve .NET Framework 4 ' te yazılmışsa bu paketin yüklenmesi gerekir.<br /><br /> Daha fazla bilgi için bkz [ F# . dil başvurusu](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|
|**Microsoft Visual Studio 2010 rapor Görüntüleyicisi**|Bu paket, Windows Forms ve ASP.NET uygulamalarına zengin veri raporlaması eklemek için kullanabileceğiniz Rapor Görüntüleyicisi denetimlerini yüklüyor.|
|**Office çalışma zamanı için Microsoft Visual Studio 2010 (x86 ve x64)**|Visual Studio 'daki Office geliştirici araçları, Microsoft Office ile özelleştirilmiş iş çözümleri oluşturmaya yönelik kullanımı kolay ve tümleşik araçlar sunar. Office uygulamalarını Kullanıcı arabirimi olarak kullanan yönetilen ve akıllı istemci çözümleri oluşturabilirsiniz. Araçlar, geliştiricilerin dağıtımı ve bakımı kolay olan güvenli çözümler oluşturmalarına olanak tanır.<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce kullanarak Office çözümü yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|
|**SQL Server 2005 Express Sürüm SP2 (x86)**|Bu paket, [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]tabanlı bir veritabanı uygulaması olan Microsoft SQL Server 2005 Express Edition SP2 'yi yüklüyor. SQL Server Express, Microsoft SQL Server masaüstü altyapısının (MSDE) yerini alır. SQL Server Express ücretsizdir ve yeniden dağıtılabilir (sözleşmeye tabi olabilir) ve hem istemci veritabanı hem de temel sunucu veritabanı olarak çalışır. Bu, aşağıdaki farklar dışında SQL Server 2005 ile aynıdır:<br /><br /> -Kurumsal özellik desteği yok.<br />-Bir CPU ile sınırlıdır.<br />arabellek havuzu için-1 gigabayt (GB) bellek sınırı.<br />-4 GB veritabanları için boyut üst sınırı.|
|**SQL Server 2008 Express**|Bu paket, bir Microsoft SQL Server 2008 Microsoft SQL Server 2008 Express ücretsiz sürümü olan, küçük Web, sunucu veya masaüstü uygulamalarına yönelik ideal bir veritabanıdır. Geliştirme ve üretim için ücretsiz olarak kullanılabilir. SQL Server 2008 Express uygulamasını uygulamayla dağıtmak için ücretsiz bir kayıt gereklidir.<br /><br /> Önyükleyicinin davranışı şunlardır:<br /><br /> -Bilgisayarda zaten SQL Server 2008 Express veya üzeri varsa, bilgisayar SQL Server 2008 Express veya sonraki bir sürümde kalır.<br />-Bilgisayarda SQL Server 2008 Express veya sonraki bir sürümü yoksa, paket SQL Server 2008 Express SP1 'in en son sürümünü yüklenir.<br /><br /> SQL Server 2008 Express hakkında daha fazla bilgi edinmek için [http://go.microsoft.com/fwlink/?LinkId=183586](https://www.microsoft.com/sqlserver/2008/en/us/express.aspx)ziyaret edin.|
|**Visual C++ 2010 çalışma zamanı KITAPLıKLARı (IA64)**|Bu paket, Microsoft Windows C++ işletim sistemi için programlama yordamları sağlayan Itanium mimarisine yönelik görsel çalışma zamanı kitaplıklarını yüklemektedir. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatikleştirin.<br /><br /> Daha fazla bilgi için bkz. [C çalışma zamanı kitaplığı başvurusu](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Visual C++ 2010 çalışma zamanı kitaplıkları (x64)**|Bu paket, Microsoft Windows C++ işletim sistemi için programlama yordamları sağlayan x64 işletim sistemleri için görsel çalışma zamanı kitaplıklarını kurar. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatikleştirin.<br /><br /> Daha fazla bilgi için bkz. [C çalışma zamanı kitaplığı başvurusu](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Visual C++ 2010 çalışma zamanı kitaplıkları (x86)**|Bu paket, Microsoft Windows C++ işletim sistemi için programlama yordamları sağlayan x86 işletim sistemleri için görsel çalışma zamanı kitaplıklarını kurar. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatikleştirin.<br /><br /> Daha fazla bilgi için bkz. [C çalışma zamanı kitaplığı başvurusu](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Windows Installer 3,1**|Bu paket, Windows Installer Kurulum projelerinin yüklenmesine izin veren Microsoft Windows Installer yeniden dağıtılabilir sürüm 3,1 ' i yüklüyor. Windows Server 2003 SP1 ve üzeri sürümlerde önceden yüklenmiştir.<br /><br /> Varsayılan olarak, bu öğe seçilidir.|
|**Windows Installer 4,5**|Bu paket, Windows Installer Kurulum projelerinin yüklenmesine izin veren Microsoft Windows Installer yeniden dağıtılabilir sürüm 4,5 ' i yüklüyor.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Yayımlama sayfası, proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md) [uygulama dağıtımı önkoşulları](../../deployment/application-deployment-prerequisites.md) [](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287) [64 bit uygulamalar Için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md) .NET Framework [Visual Studio çoklu hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md)
