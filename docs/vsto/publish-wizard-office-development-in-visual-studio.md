---
title: Yayımlama Sihirbazı (Visual Studio 'da Office geliştirme)
description: Yayımlama sihirbazını, çözüm dosyalarını belirtilen bir konuma kopyalamak, bildirim dosyalarını oluşturmak ve Visual Studio 'da bir kurulum programı oluşturmak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528019"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Yayımlama Sihirbazı (Visual Studio 'da Office geliştirme)
  Çözüm dosyalarını belirtilen bir konuma kopyalamak için **Yayımlama sihirbazını** kullanın, bildirim dosyalarını oluşturun ve bir kurulum programı oluşturun.

 Bu sihirbaza erişmek için, **Oluştur** menüsünde, *SolutionName* **Yayımla** ' yı seçin. **Yayımla sihirbazına** de **Çözüm Gezgini** erişebilirsiniz. Proje düğümü için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

 Aşağıdaki her bölümde, sihirbazın bir sayfası açıklanmaktadır.

## <a name="where-do-you-want-to-publish-the-application"></a>Uygulamayı nerede yayımlamak istiyorsunuz?
 **Bu uygulamanın yayımlanacağı konumu belirtin** Gerekli. Yayımlama konumu, **Yayımlama sihirbazının** bildirimler, derlemeler, geçici sertifika ve diğer dosyalar ile derleme gibi çözüm dosyalarını kopyaladığı dizindir. Bu dizine yazma erişiminizin olması gerekir.

 Konumu bir disk yolu, dosya paylaşma, FTP sitesi veya Web sitesi URL 'SI olarak yazın veya konuma gitmek için **Araştır** düğmesine tıklayın. Yol şu biçimlerde olabilir:

- *C:\deploy\myapplication* veya *\MyApplication* gibi standart Windows biçiminde göreli veya mutlak bir yol.

- *\\ \ServerName\MyApplication \\* gibi bir evrensel adlandırma kuralı (UNC) yolu.

- Bir Web sitesinin URL 'SI, örneğin `http://www.contoso.com/MyApplication` .

  Varsayılan olarak, yayımlama konumu *http://localhost/projectname/* IIS yüklü veya IIS yüklü değilse Yayımla \ dizinine sahipsiniz.

> [!NOTE]
> Hedef bilgisayarda Windows Vista çalışıyorsa daha fazla dikkat edilecek noktalar vardır. Yerel yayımlama seçeneğini kullanmak için Windows Vista bilgisayarında bir yönetici olmanız gerekir. Ayrıca, IIS 'nin yüklü olup olmamasından bağımsız olarak varsayılan konum her zaman *Yayımla \\* dizinidir.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında varsayılan yükleme yolu nedir?
 Yükleme yolu isteğe bağlıdır. İsterseniz yükleme yolunu daha sonra ayarlayabilirsiniz. Ayrıntılar için bkz. [nasıl yapılır: bir Office çözümünün yükleme yolunu değiştirme](/previous-versions/bb608626(v=vs.110)).

 Yükleme yolu, son kullanıcının özelleştirmeyi yükleyeceksiniz. Ayrıca, çözümün güncelleştirmeleri denetlemek için kullanacağı yoldur. Uygulama, önceki sayfada **Bu uygulamayı yayımlamak için konumu belirtin** kutusunda girdiğiniz konum ile aynı değilse, **Yayımlama Sihirbazı** çözümü bu konuma dağıtmaz.

 **Bir Web sitesinden** Son Kullanıcıların çözümü yüklemek için takip edecek URL 'YI belirtin.

 **UNC yolundan veya dosya paylaşımından** Son Kullanıcıların çözümü yüklemek için takip edecek UNC yolunu belirtin.

 **BIR CD-ROM veya DVD-ROM ' d** a Bu seçenek, yükleme yolu gerektirmez.

 Visual Studio, CD veya DVD 'yi yazamıyor. Çıktıyı el ile bir CD veya DVD 'ye kopyalamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Visual Studio 'da Office geliştirme &#40;yayımlama sayfası, proje Tasarımcısı&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)