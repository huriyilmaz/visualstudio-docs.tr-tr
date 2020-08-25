---
title: Entity Framework & Visual Studio 2019 ile Web uygulaması ASP.NET Core
titleSuffix: ''
description: ASP.NET Core Web uygulaması oluşturmadan önce ilk adım olarak, bu video öğreticisiyle Visual Studio 2019 'yi yüklemeyi ve adım adım yönergeleri öğrenin.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f6d069bfa462b8aa75fc9247c08b3662c4a445fd
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801808"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Öğretici: Visual Studio 2019 ile Entity Framework kullanarak ilk ASP.NET Core uygulamanızı oluşturma

Bu öğreticide, verileri kullanan bir ASP.NET Core Web uygulaması oluşturacaksınız ve Azure 'a dağıtırsınız. Bu öğretici aşağıdaki adımlardan oluşur:

- [1. Adım: Visual Studio 2019 'Yi yükler](#step-1-install-visual-studio-2019)
- [2. Adım: ilk ASP.NET Core Web uygulamanızı oluşturma](tutorial-aspnet-core-ef-step-02.md)
- [3. Adım: Entity Framework kullanarak verilerle çalışma](tutorial-aspnet-core-ef-step-03.md)
- [4. Adım: ASP.NET Core uygulamanızdan bir Web API 'SI kullanıma sunma](tutorial-aspnet-core-ef-step-04.md)
- [5. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>1. Adım: Visual Studio 2019 'Yi yükler

Bu video öğreticisiyle Visual Studio 2019 ' i nasıl yükleyeceğinizi ve adım adım yönergeleri öğrenin. Visual Studio 'Yu önceden yüklediyseniz [2. Adım: ilk ASP.NET Core Web uygulamanızı oluşturma](tutorial-aspnet-core-ef-step-02.md)bölümüne atlayın.

_Visual Studio 'Yu yüklemek ve ilk ASP.NET Core uygulamanızı oluşturmak için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Yükleyiciyi indirin

Yükleyiciyi bulmak için [VisualStudio.com](https://visualstudio.com) adresine gidin. Visual Studio 2019 bağlantısını bulun ve indirmeyi başlatmak için tıklatın. Visual Studio 'nun ücretsiz bir sürümü için Visual Studio Community ' yi seçin.

## <a name="start-the-installer"></a>Yükleyiciyi Başlat

İndirme tamamlandıktan sonra, yükleyiciyi başlatmak için **Çalıştır** ' a tıklayın.

![Visual Studio 2019 yükleyicisi](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>İş yüklerini seçin

Visual Studio birçok farklı geliştirme türü için kullanılabilir ve iş yükleri, derlemek istediğiniz uygulama türleri için ihtiyaç duyduğunuz her şeyi indirmeyi kolaylaştırır. Şimdilik **ASP.net ve Web geliştirme** ve **.NET Core platformlar arası geliştirme** iş yüklerini seçin. Ek iş yüklerini ve bileşenleri yüklemek için yükleyiciyi daha sonra her zaman yeniden başlatabilirsiniz.

![Visual Studio 2019 Iş yüklerini seçin](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Yükleme

**Yükle** ' ye tıklayın ve yükleyicinin Visual Studio 'yu indirip yüklemesine izin verin.

## <a name="run-visual-studio-for-the-first-time"></a>Visual Studio 'Yu ilk kez çalıştırın

Yükleyici tamamlandığında Visual Studio otomatik olarak başlamalıdır. Bunlarla ilişkili bazı iyi özellikler içeren oturum açmanız istenebilir, ancak şimdilik bunu daha sonra yapmayı tercih edebilirsiniz. Daha sonra tema ve geliştirme ayarlarınızı seçebilirsiniz. Bu seçimleri yaptıktan sonra ilk projenizi başlatmaya başlayabilirsiniz. **Yeni proje oluştur ' a** tıklayın ve ardından **ASP.NET Core Web uygulaması**' nı seçin.

![Visual Studio 2019 yeni ASP.NET Core Web uygulaması projesi oluştur](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>ASP.NET Core proje türlerini keşfet

Proje adınızı ve konumunuzu seçip **Oluştur**' u seçin. Şimdi ASP.NET Core uygulamanız için kullanılacak şablonu seçin. Aşağıdaki seçeneklerden birini belirtebilirsiniz:

- Olmamalıdır. Sıfırdan başlayıp başlayabilmenizi sağlayan boş bir proje şablonu.
- 'Sindeki. Web API 'Leri için en iyisi.
- Web uygulaması. Razor Pages ile oluşturulan standart bir ASP.NET Core Web uygulaması.
- Web uygulaması (Model-View-Controller). Model-View-Controller modelini kullanan standart bir ASP.NET Core Web uygulaması.
- Angular.
- React.js.
- React.js/Redux.
- Razor sınıf kitaplığı. Razor varlıklarını projeler arasında paylaşmak için kullanılır.

Çoğu proje şablonu için bir kutuyu işaretleyerek Docker desteğini etkinleştirmeyi de seçebilirsiniz. Kimlik doğrulamasını Değiştir düğmesine tıklayarak da kimlik doğrulama desteği ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:

- Kimlik doğrulaması yok.
- Bireysel kullanıcı hesapları. Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
- İş veya okul hesapları. Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
- Windows kimlik doğrulaması. İntranet uygulamaları için uygun.

Kimlik doğrulaması olmadan standart Web uygulaması şablonunu seçin ve **Oluştur**' a tıklayın.

![Visual Studio 2019 ASP.NET Core projesi seçeneklerini belirleyin](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Sonraki adımlar

Sonraki videoda, ilk ASP.NET Core projeniz hakkında daha fazla bilgi edineceksiniz.

[Öğretici: Ilk ASP.NET Core Web uygulamanızı oluşturma](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: C# ve ASP.NET Core kullanmaya başlama](tutorial-aspnet-core.md) Video adım adım olmadan daha ayrıntılı bir öğretici
