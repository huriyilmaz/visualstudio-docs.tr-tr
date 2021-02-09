---
title: Önkoşullar İletişim Kutusu
description: Önkoşullar iletişim kutusu hangi önkoşul bileşenlerinin yüklendiğini, bunların nasıl yüklendiğini ve paketlerin hangi sırayla yükleneceğini belirtir.
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78d5f4f00a81fccf573e69797b9d528ee61ffdc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932065"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu

**Önkoşullar** iletişim kutusu hangi önkoşul bileşenlerinin yüklendiğini, bunların nasıl yüklendiğini ve paketlerin hangi sırayla yükleneceğini belirtir.

![Visual Studio 'da Önkoşullar iletişim kutusu](media/prerequisites-dialog-box.png)

İletişim kutusuna erişmek için, **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje**  >  **özellikleri**' ni seçin. **Proje Tasarımcısı** göründüğünde, **Yayımla** sekmesini seçin ve ardından **Önkoşullar**' ı seçin. Kurulum projeleri için, **Proje** menüsünde **Özellikler**' e tıklayın. **Özellik sayfaları** iletişim kutusu göründüğünde, **Önkoşullar**' ı tıklatın.

## <a name="uielement-list"></a>UIElement listesi

|Öğe|Açıklama|
|-------------|-----------------|
|**Önkoşul bileşenlerini yüklemek için Kurulum programı oluşturma**|Uygulamanızın uygulama Kurulum programında (*Setup.exe*) Önkoşul bileşenlerini içerir, böylece uygulamanız, bağımlılık sırasına göre yüklenir. Varsayılan olarak, bu seçenek seçilidir. Seçili değilse *Setup.exe* oluşturulmaz.|
|**Hangi önkoşulların yükleneceğini seçin**|.NET Framework ve C++ çalışma zamanı kitaplıkları gibi bileşenlerin yüklenip yüklenmeyeceğini belirtir.<br /><br />Örneğin, **SQL Server 2012 Express**' in yanındaki onay kutusunu seçerek, Kurulum programının bu bileşenin hedef bilgisayarda yüklü olup olmadığını doğrulaması gerektiğini ve değilse yüklemesi gerektiğini belirtirsiniz.<br /><br />Her önkoşul paketiyle ilgili ayrıntılı bilgi için bkz. [Önkoşul bilgileri](#prerequisites-information).|
|**Önkoşulları bileşen satıcısının Web sitesinden indir**|Önkoşul bileşenlerinin satıcının Web sitesinden yükleneceğini belirtir. Bu varsayılan seçenektir.|
|**Önkoşulları Uygulamam ile aynı konumdan indir**|Önkoşul bileşenlerinin uygulamayla aynı konumdan yükleneceğini belirtir. Bu, tüm önkoşul paketlerini yayımlama konumuna kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
|**Önkoşulları aşağıdaki konumdan indirin**|Önkoşul bileşenlerinin girdiğiniz konumdan yükleneceğini belirtir. Bir konum seçmek için, **tarayıcı** düğmesini kullanabilirsiniz.|

> [!NOTE]
> Önkoşulları nereye koyabileceğiniz hakkında bilgi için bkz. [önyükleyici paketleri oluşturma](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Önkoşul bilgileri

**Önkoşullar** iletişim kutusunda görünen önkoşul bileşenleri, aşağıdaki listede yer alan uygulamalardan farklı görünebilir. **Önkoşullar Iletişim kutusunda** listelenen önkoşul paketleri, iletişim kutusunu ilk açışınızda otomatik olarak ayarlanır. Projenin hedef çerçevesini daha sonra değiştirirseniz, yeni hedef Framework 'ü eşleştirmek için önkoşulları el ile seçmeniz gerekir.

|Öğe|Açıklama|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Bu paket aşağıdakileri yükleyerek:<br /><br /> -2,0, 3,0 ve 3,5 sürümlerini .NET Framework.<br />-32-bit (x86) ve 64 bit (x64) işletim sistemlerindeki tüm .NET Framework sürümleri için destek.<br />-Paketiyle birlikte yüklenen her bir .NET Framework sürümü için dil paketleri.<br />-.NET Framework 2,0 ve 3,0 için hizmet paketleri.<br /><br /> .NET Framework 3,0, Windows Vista 'da bulunur ve Visual Studio 'da .NET Framework 3,5 bulunur. .NET Framework 3,5, 32 bit işletim sistemleri için derlenen ve hedef Framework 'ün **.NET Framework 3,5** olarak ayarlandığı ve 64-bit işletim sistemleri için derlenen Visual Basic ve c# projelerinin için derlenmiş tüm Visual Basic ve c# projeleri için gereklidir. (IA64 desteklenmez.) Visual Basic ve C# projelerinin varsayılan olarak herhangi bir CPU mimarisi için derlendiğini unutmayın. Daha fazla bilgi için bkz. [framework hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md) ve [64-bit uygulamalar için önkoşulları dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4. x**|Bu paket, hem x86 hem de x64 platformları için 4. x .NET Framework.|
|**SQL Server 2014 için Microsoft System CLR Types (x64 ve x86)**|Bu paket x64 veya x86 için SQL Server 2014 için Microsoft System CLR türlerini kurar.|
|**SQL Server 2008 R2 Express**|Bu paket, bir Microsoft SQL Server 2008 R2 ücretsiz sürümü olan Microsoft SQL Server 2008 R2 Express, küçük Web, sunucu veya masaüstü uygulamalarına yönelik ideal bir veritabanıdır. Geliştirme ve üretim için ücretsiz olarak kullanılabilir.|
|**SQL Server 2012 Express**|Bu paket Microsoft SQL Server 2012 Express 'ı yüklüyor.|
|**SQL Server 2012 Express LocalDB**|Bu paket Microsoft SQL Server 2012 Express LocalDB 'yi yüklüyor.|
|**Visual C++ "14" çalışma zamanı kitaplıkları (ARM)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan Itanium mimarisine yönelik Visual C++ çalışma zamanı kitaplıklarını yükleme. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatik hale getirir.<br /><br /> Daha fazla bilgi için bkz. [C Run-Time kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" çalışma zamanı kitaplıkları (x64)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan x64 işletim sistemlerine yönelik Visual C++ çalışma zamanı kitaplıklarını yükleme. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatik hale getirir.<br /><br /> Daha fazla bilgi için bkz. [C Run-Time kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" çalışma zamanı kitaplıkları (x86)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan x86 işletim sistemleri için Visual C++ çalışma zamanı kitaplıklarını yükleme. Bu yordamlar, C ve C++ dilleri tarafından sağlanmayan yaygın programlama görevlerinin çoğunu otomatik hale getirir.<br /><br /> Daha fazla bilgi için bkz. [C Run-Time kitaplığı başvurusu](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Ayrıca bkz.

- [Yayın Sayfası, Proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md)
- [Uygulama dağıtımı önkoşulları](../../deployment/application-deployment-prerequisites.md)
- [64 bit Uygulamalar için Önkoşulları Dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Çerçeve hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md)
