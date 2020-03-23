---
title: Önkoşullar İletişim Kutusu
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ecbba1a1c5e8670fd9adcafdfed8cec21dd3912
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567911"
---
# <a name="prerequisites-dialog-box"></a>Önkoşullar iletişim kutusu

**Önkoşullar** iletişim kutusu, hangi ön koşul bileşenlerinin yüklendiği, nasıl yüklendiği ve paketlerin hangi sırayla yüklendiği belirtilir.

![Visual Studio'da önkoşullar iletişim kutusu](media/prerequisites-dialog-box.png)

İletişim kutusuna erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin ve ardından **Project** > **Properties'i**seçin. Proje **Tasarımcısı** göründüğünde, **Yayımla** sekmesini seçin ve ardından **Önkoşullar'ı**seçin. Kurulum projeleri **için, Proje** menüsünde **Özellikler'i**tıklatın. Özellik **Sayfaları** iletişim kutusu göründüğünde, **Önkoşullar'ı**tıklatın.

## <a name="uielement-list"></a>UIElement listesi

|Öğe|Açıklama|
|-------------|-----------------|
|**Ön koşul bileşenlerini yüklemek için kurulum programı oluşturma**|Uygulamanızın Kurulum programındaki ön koşul bileşenlerini *(Setup.exe)* içerir, böylece uygulamanızdan önce bağımlılık sırasına göre yüklenirler. Varsayılan olarak, bu seçenek seçilidir. Seçili değilse, *Setup.exe* oluşturulmaz.|
|**Hangi ön koşulların yüklenmesini seçin**|.NET Framework ve C++ çalışma zamanı kitaplıkları gibi bileşenlerin yüklenip yüklenmeyeceğini belirtir.<br /><br />Örneğin, **SQL Server 2012 Express'in**yanındaki onay kutusunu seçerek, Kurulum programının bu bileşenin hedef bilgisayara yüklü olup olmadığını doğrulaması ve yoksa yüklemesi gerektiğini belirtirsiniz.<br /><br />Her ön koşul paketi hakkında ayrıntılı bilgi için, [Önkoşullar bilgilerine](#prerequisites-information)bakın.|
|**Bileşen satıcısının web sitesinden ön koşulları indirin**|Ön koşul bileşenlerinin satıcının web sitesinden yüklenmesini belirtir. Bu varsayılan seçenektir.|
|**Ön koşulları uygulamamla aynı konumdan indirin**|Ön koşul bileşenlerinin uygulamayla aynı konumdan yüklenmesini belirtir. Bu, yayımlama konumuna tüm ön koşul paketlerini kopyalar. Bu seçeneğin çalışması için önkoşul paketleri geliştirme bilgisayarında olmalıdır.|
|**Ön koşulları aşağıdaki konumdan indirin**|Ön koşul bileşenlerinin girdiğiniz konumdan yüklenmesini belirtir. Bir konum seçmek için **Gözat** düğmesini kullanabilirsiniz.|

> [!NOTE]
> Ön koşulların nereye konacağı hakkında bilgi için [bkz.](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages)

## <a name="prerequisites-information"></a>Önkoşullar bilgileri

**Önkoşullar** iletişim kutusunda görünen ön koşul bileşenleri aşağıdaki listedekilerden farklı olabilir. **Önkoşul İletişim Kutusu'nda** listelenen ön koşul paketleri, iletişim kutusunu ilk açtığınız anda otomatik olarak ayarlanır. Daha sonra projenin hedef çerçevesini değiştirirseniz, yeni hedef çerçeveyle eşleşecek ön koşulları el ile seçmeniz gerekir.

|Öğe|Açıklama|
|-------------|-----------------|
|**.NET Framework 3.5 SP1 **|Bu paket aşağıdakileri yükler:<br /><br /> - .NET Framework sürümleri 2.0, 3.0 ve 3.5.<br />- 32 bit (x86) ve 64 bit (x64) işletim sistemlerindeki tüm .NET Framework sürümleri için destek.<br />- Paketle birlikte yüklenen her .NET Framework sürümü için dil paketleri.<br />- .NET Framework 2.0 ve 3.0 için servis paketleri.<br /><br /> .NET Framework 3.0 Windows Vista'ya, .NET Framework 3.5 ise Visual Studio'ya dahildir. .NET Framework 3.5, 32 bit işletim sistemleri için derlenen ve hedef çerçevenin **.NET Framework 3.5**olarak ayarlandığı tüm Visual Basic ve C# projeleri ve 64 bit işletim sistemleri için derlenen Visual Basic ve C# projeleri için gereklidir. (IA64 desteklenmez.) Visual Basic ve C# projelerinin varsayılan olarak herhangi bir CPU mimarisi için derlenmiş olduğunu unutmayın. Daha fazla bilgi için, [Çerçeve hedefleme genel bakış](../../ide/visual-studio-multi-targeting-overview.md) ve [64 bit uygulamalar için ön koşulları dağıtma'ya](../../deployment/deploying-prerequisites-for-64-bit-applications.md)bakın.|
|**Microsoft .NET Framework 4.x**|Bu paket, hem x86 hem de x64 platformları için .NET Framework 4.x'i yükler.|
|**SQL Server 2014 için Microsoft System CLR Türleri (x64 ve x86)**|Bu paket, SQL Server 2014 için X64 veya x86 için Microsoft System CLR Types yükler.|
|**SQL Server 2008 R2 Express**|Bu paket, küçük web, sunucu veya masaüstü uygulamaları için ideal bir veritabanı olan Microsoft SQL Server 2008 R2'nin ücretsiz bir sürümü olan Microsoft SQL Server 2008 R2'yi yükler. Bu geliştirme ve üretim için ücretsiz olarak kullanılabilir.|
|**SQL Server 2012 Express**|Bu paket Microsoft SQL Server 2012 Express yükler.|
|**SQL Server 2012 Express LocalDB**|Bu paket Microsoft SQL Server 2012 Express LocalDB yükler.|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (ARM)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan Itanium mimarisi için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar, C ve C++ dilleri tarafından sağverilmeyecek birçok yaygın programlama görevini otomatikleştirir.<br /><br /> Daha fazla bilgi için [C Run-Time Kitaplığı Başvurusu'na](/cpp/c-runtime-library/c-run-time-library-reference)bakın.|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (x64)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan x64 işletim sistemleri için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar, C ve C++ dilleri tarafından sağverilmeyecek birçok yaygın programlama görevini otomatikleştirir.<br /><br /> Daha fazla bilgi için [C Run-Time Kitaplığı Başvurusu'na](/cpp/c-runtime-library/c-run-time-library-reference)bakın.|
|**Visual C++ "14" Çalışma Zamanı Kitaplıkları (x86)**|Bu paket, Microsoft Windows işletim sistemi için programlama yordamları sağlayan x86 işletim sistemleri için Visual C++ çalışma zamanı kitaplıklarını yükler. Bu yordamlar, C ve C++ dilleri tarafından sağverilmeyecek birçok yaygın programlama görevini otomatikleştirir.<br /><br /> Daha fazla bilgi için [C Run-Time Kitaplığı Başvurusu'na](/cpp/c-runtime-library/c-run-time-library-reference)bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Yayın Sayfası, Proje Tasarımcısı](../../ide/reference/publish-page-project-designer.md)
- [Uygulama Dağıtımının Önkoşulları](../../deployment/application-deployment-prerequisites.md)
- [64 bit Uygulamalar için Önkoşulları Dağıtma](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Çerçeve hedeflemegenel bakış](../../ide/visual-studio-multi-targeting-overview.md)
