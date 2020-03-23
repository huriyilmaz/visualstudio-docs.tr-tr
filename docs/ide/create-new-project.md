---
title: Yeni bir proje oluşturma
ms.date: 03/19/2019
ms.topic: conceptual
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77a6a33a1dde4d779a56c9ee559ecfd3b20dfbfb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585476"
---
# <a name="create-a-new-project-in-visual-studio"></a>Visual Studio'da yeni bir proje oluşturun

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>Yeni Proje iletişim kutusunu açma

Visual Studio 2017'de yeni bir proje oluşturmanın birçok yolu vardır. Başlat sayfasında, **Arama projesi şablonları** kutusuna proje şablonlarının adını yazabilir veya **Yeni Proje** iletişim kutusunu açmak için yeni **proje** oluştur bağlantısını seçebilirsiniz. Başlat sayfasının yanı sıra, menü çubuğunda**Yeni** > **Proje** **Dosyası'nı** > seçebilir veya araç çubuğundaki **Yeni Proje** düğmesini tıklatabilirsiniz.

![Yeni > Projesi> başlat sayfası ve Dosya](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

Yeni **Proje** iletişim kutusunda, kullanılabilir proje şablonları **Şablonlar** kategorisi altındaki bir listede görünür. Şablonlar Visual C#, JavaScript ve Azure Veri Gölü gibi programlama dili ve proje türüne göre düzenlenir.

![Yeni proje iletişim kutusu](./media/vside-newproject-templates-list.png)

> [!NOTE]
> Görünen kullanılabilir dillerin ve proje şablonlarının listesi, çalıştırdığınız Visual Studio sürümüne ve yüklenen iş yüklerine bağlıdır. Ek iş yüklerini nasıl yükleyeceğiz hakkında bilgi edinmek için, [iş yüklerini ve bileşenleri ekleyerek veya kaldırarak Görsel Stüdyo'da Değiştir'e](../install/modify-visual-studio.md)bakın.

Dil adının yanındaki üçgeni tıklatıp ardından proje kategorisi (Windows Desktop gibi) seçerek kullanmak istediğiniz programlama dili için şablonlistesini gösterin.

Aşağıdaki resim, Visual C# .NET Core projeleri için kullanılabilir proje şablonlarını gösterir:

![Proje şablonları](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>Projenizi yapılandırın

**Ad** kutusuna yeni proje için bir ad girin. Projeyi bilgisayarınızdaki varsayılan konuma kaydedebilir veya başka bir konum bulmak için **Gözat** düğmesini tıklatabilirsiniz. Ayrıca bir çözüm adı seçebilir veya yeni projeyi Git deposuna ekleyebilirsiniz **(Kaynak Denetimine Ekle'yi**seçerek).

Çözüm ve proje oluşturmak için **Tamam'ı** tıklatın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>Yeni proje sayfası oluştur'u açma

Visual Studio 2019'da yeni bir proje oluşturmanın birçok yolu vardır. Visual Studio'yu ilk açtığınızda, başlangıç penceresi görüntülenir ve buradan **yeni bir proje oluştur'u**seçebilirsiniz.

![VS 2019'da başlangıç penceresinden yeni bir proje oluşturma](media/vs-2019/start-window-create-new-project.png)

Visual Studio geliştirme ortamı zaten açıksa, menü çubuğunda **Yeni** > **Proje** **Dosyası'nı** > seçerek veya araç çubuğundaki **Yeni Proje** düğmesini tıklatarak yeni bir proje oluşturabilirsiniz.

![Visual Studio 2019'da Yeni Proje düğmesi](media/vs-2019/new-project-button.png)

## <a name="select-a-template-type"></a>Şablon türü seçin

Yeni **bir proje oluştur** sayfasında, sol tarafta en son seçili şablonlarınızın listesi görüntülenir. Şablonlar en son *kullanılana*göre sıralanır.

En son kullanılan şablonlardan seçim yapmadıysanız, kullanılabilir tüm proje şablonlarını **Dile** (örneğin C# veya C++), **Platforma** (örneğin, Windows veya Azure) ve **Proje türüne** (örneğin, Masaüstü veya Web) göre filtreleyebilirsiniz. Ayrıca, arama kutusuna arama metni girerek şablonları daha fazla filtreleyebilir, **örneğin, asp.net.**

![Visual Studio 2019'da proje şablonu filtreleri](media/vs-2019/create-new-project-filters.png)

Her şablonun altında görünen etiketler üç açılır filtreye (Dil, Platform ve Proje türü) karşılık gelir.

> [!TIP]
> Aradığınız şablonu görmüyorsanız, Visual Studio için bir iş yükü eksik olabilir. Ek iş yükleri yüklemek için (örneğin, .NET ile **Azure Geliştirme** veya **Mobil Geliştirme),** Visual Studio Installer'ı açmak için **daha fazla araç ve özellik** yükle bağlantısını tıklatın. Buradan, yüklemek istediğiniz iş yüklerini seçin ve sonra **Değiştir'i**seçin. Bundan sonra, seçim için ek proje şablonları kullanılabilir olacaktır.
>
> ![VS 2019'da daha fazla araç ve özellik bağlantısı yükleyin](media/vs-2019/install-more-tools-features.png)

Bir şablon seçin ve sonra **İleri'yi**tıklatın.

## <a name="configure-your-project"></a>Projenizi yapılandırın

**Yeni proje sayfanızı YapılandırMa'da** projenize (ve çözümünüzün) adını verme, bir disk konumu seçme ve bir Framework sürümü seçme (seçtiğiniz şablona uygunsa) seçenekleri vardır.

![VS 2019'da yeni proje sayfanızı yapılandırın](media/vs-2019/configure-new-project.png)

> [!NOTE]
> Visual Studio'da zaten açık bir proje veya çözüm olduğunda yeni bir proje oluşturursanız, ek bir yapılandırma seçeneği kullanılabilir. Yeni bir çözüm oluşturmayı veya yeni projeyi zaten açık olan çözüme eklemeyi seçebilirsiniz.
>
> ![VS 2019'da yeni çözüm oluşturun veya varolan çözüme ekleyin](media/vs-2019/configure-new-project-solution.png)

Yeni proje oluşturmak için **Oluştur'u** tıklatın.

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>Çözüme ek projeler ekleme

Bir çözüme ek bir proje eklemek istiyorsanız, **Çözüm Gezgini'ndeki** çözüm düğümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](creating-solutions-and-projects.md)
