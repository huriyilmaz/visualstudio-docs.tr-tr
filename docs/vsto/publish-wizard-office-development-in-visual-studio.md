---
title: Yayımlama sihirbazı (Office geliştirme Visual Studio)
description: Çözüm dosyalarını belirtilen bir konuma kopyalamak, bildirim dosyalarını oluşturmak ve bir Kurulum programı oluşturmak için Yayımlama Sihirbazı'nı nasıl kullanabileceğinizi Visual Studio.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5078179f4dbe0ba65ada1ec0dee6e3aeeefbc094
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099548"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Yayımlama sihirbazı (Office geliştirme Visual Studio)
  Çözüm dosyalarını **belirtilen bir** konuma kopyalamak, bildirim dosyalarını oluşturmak ve bir Kurulum programı oluşturmak için Yayımlama Sihirbazı'nı kullanın.

 Bu sihirbaza erişmek için, Derleme **menüsünde ÇözümAdı** Yayımla'yı  *seçin.* Yayımlama Sihirbazı'nı kullanarak  **da Çözüm Gezgini.** Proje düğümünün kısayol menüsünü açın ve Yayımla'yı **seçin.**

 Aşağıdaki her bölümde sihirbazın bir sayfası açıklanmıştır.

## <a name="where-do-you-want-to-publish-the-application"></a>Uygulamayı nerede yayımlamak istiyorsunuz?
 **Bu uygulamayı yayımlamak için konumu belirtin** Gerekli. Yayımlama konumu, Yayımlama Sihirbazı'nın derlemeden bildirim, derleme, geçici sertifika ve diğer dosyalar gibi çözüm dosyalarını kopya ettiği dizindir.  Bu dizine yazma erişiminiz olmalıdır.

 Konumu disk yolu, dosya paylaşımı, FTP sitesi veya web sitesi  URL'si olarak yazın veya Gözat düğmesine tıklayarak konuma göz atabilirsiniz. Yol şu biçimlerde olabilir:

- *C:\Deploy\MyApplication* veya *\MyApplication* gibi standart bir Windows göreli veya mutlak yol.

- *\\ \ServerName\MyApplication \\* gibi bir Evrensel Adlandırma Kuralı (UNC) yolu.

- Gibi bir web sitesinin `http://www.contoso.com/MyApplication` URL'si.

  Varsayılan olarak, yayımlama konumu IIS yüklüyse veya IIS yüklü değilse *http://localhost/projectname/* publish\ dizinidir.

> [!NOTE]
> Hedef bilgisayar Vista'da çalışıyorsa daha fazla Windows vardır. Yerel yayımlama seçeneğini kullanmak için Windows Vista bilgisayarda yönetici olmak gerekir. Ayrıca, IIS yüklü olup olmadığınız *ne olursa olsun \\* varsayılan konum her zaman yayımlama dizinidir.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında varsayılan yükleme yolu nedir?
 Yükleme yolu isteğe bağlıdır. Tercih ederseniz yükleme yolunu daha sonra ayarlayabilirsiniz. Ayrıntılar için [bkz. Nasıl: Bir çözüm için yükleme Office değiştirme.](/previous-versions/bb608626(v=vs.110))

 Yükleme yolu, son kullanıcının özelleştirmeyi yükleyecek olduğu dizindir. Ayrıca çözümün güncelleştirmeleri denetlemesi için de bu yolu kullanır. Yol **önceki** sayfada bu uygulamayı yayımlayacak konumu belirtin kutusuna girdiğiniz yolla aynı  değilse Yayımlama Sihirbazı çözümü bu konuma dağıtmaz.

 **Bir Web sitesinden** Çözümü yüklemek için son kullanıcıların takip edecekleri URL'yi belirtin.

 **UNC yolundan veya dosya paylaşımından** Son kullanıcıların çözümü yüklemek için takip edecekleri UNC yolunu belirtin.

 **CD-ROM veya DVD-ROM'dan** Bu seçenek bir yükleme yolu gerektirmez.

 Visual Studio CD veya DVD yazmaz. Çıkışı bir CD veya DVD'ye el ile kopyalamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office kullanarak bir Office çözümü ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Yayımlama Sayfası, Project Tasarımcısı &#40;Office geliştirme Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)