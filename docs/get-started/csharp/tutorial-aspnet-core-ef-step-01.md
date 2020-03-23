---
title: ASP.NET Core web uygulaması ile Entity Framework & Visual Studio 2019
titleSuffix: ''
description: ASP.NET Core web uygulaması oluşturmadan önceki ilk adım olarak, visual studio 2019'u bu video eğitimi ve adım adım talimatlarla nasıl yükleyin öğrenin.
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
ms.openlocfilehash: d900c0f51b14450f38caf06738739daef2549235
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580093"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Öğretici: Visual Studio 2019 ile Entity Framework'ü kullanarak ilk ASP.NET Core Uygulamanızı oluşturun

Bu eğitimde, verileri kullanan bir ASP.NET Core web uygulaması oluşturup Azure'a dağıtacaksınız. Bu öğretici aşağıdaki adımlardan oluşur:

- [Adım 1: Visual Studio 2019'u Yükleyin](#step-1-install-visual-studio-2019)
- [Adım 2: İlk ASP.NET Core web uygulamanızı oluşturun](tutorial-aspnet-core-ef-step-02.md)
- [Adım 3: Varlık Çerçevesi'ni kullanarak verilerle çalışma](tutorial-aspnet-core-ef-step-03.md)
- [Adım 4: ASP.NET Core uygulamanızdan bir web API'si açığa çıkarma](tutorial-aspnet-core-ef-step-04.md)
- [Adım 5: ASP.NET Core uygulamanızı Azure'a dağıtın](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Adım 1: Visual Studio 2019'u Yükleyin

Visual Studio 2019'u bu video eğitimi ve adım adım talimatlarla nasıl yükleyin öğrenin. Visual Studio'ya zaten yüklediyseniz, [Adım 2'ye geçin: İlk ASP.NET Core web uygulamanızı oluşturun.](tutorial-aspnet-core-ef-step-02.md)

_Bu videoyu izleyin ve Visual Studio'yı yüklemek ve ilk ASP.NET Core uygulamanızı oluşturmak için takip edin._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Yükleyiciyi İndirin

Yükleyiciyi bulmak için [visualstudio.com](https://visualstudio.com) gidin. Visual Studio 2019 bağlantısını bulun ve indirmeye başlamak için tıklayın. Visual Studio'nun ücretsiz bir sürümü için Visual Studio Community'yi seçin.

## <a name="start-the-installer"></a>Yükleyiciyi Başlat

İndirme tamamlandıktan sonra yükleyiciyi başlatmak için **Çalıştır'ı** tıklatın.

![Visual Studio 2019 Yükleyici](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>İş yüklerini seçin

Visual Studio birçok farklı geliştirme türü için kullanılabilir ve iş yükleri oluşturmak istediğiniz uygulamalar için ihtiyacınız olan her şeyi indirmenizi kolaylaştırır. Şimdilik **ASP.NET ve Web Geliştirme ve** **.NET Core platform ötesi geliştirme** iş yüklerini seçin. Ek iş yükleri ve bileşenleri yüklemek için yükleyiciyi daha sonra her zaman yeniden başlatabilirsiniz.

![Visual Studio 2019 İş Yüklerini Seçin](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Yükleme

**Yükle'yi** tıklatın ve yükleyicinin Visual Studio'yu indirmesine ve yüklemesine izin verin.

## <a name="run-visual-studio-for-the-first-time"></a>Visual Studio'yu ilk kez çalıştırın

Yükleyici bittiğinde Visual Studio otomatik olarak başlatılmalıdır. Oturum açmanız istanabilir, bu da onunla ilişkili bazı güzel özelliklere sahiptir, ancak şimdilik bunu daha sonra yapmayı seçebilirsiniz. Daha sonra tema ve geliştirme ayarlarınızı seçebilirsiniz. Bu seçimleri yaptıktan sonra, ilk projenize başlamaya hazır olacaksınız. **Yeni bir proje oluştur'u** tıklatın ve ardından Çekirdek Web Uygulaması **ASP.NET**seçin.

![Visual Studio 2019 Yeni ASP.NET Web Uygulama Projesi Oluştur](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>ASP.NET Core proje türlerini keşfedin

Proje adınızı ve konumunuzu seçebilir, ardından **Oluştur'u**seçebilirsiniz. Şimdi ASP.NET Core uygulamanız için hangi şablonu kullanacağınızı seçin. Aşağıdaki seçeneklerden birini belirtebilirsiniz:

- Boş. Sıfırdan başlamanızı sağlayan boş bir proje şablonu.
- Apı. Web API'leri için en iyisi.
- Web Uygulaması. Razor Pages ile oluşturulmuş standart ASP.NET Core web uygulaması.
- Web Uygulaması (Model-View-Controller). Model-View-Controller modelini kullanan standart ASP.NET Core web uygulaması.
- Açısal.
- Tepki.js.
- React.js / Redux.
- Razor Sınıf Kütüphanesi. Razor varlıklarını projeler arasında paylaşmak için kullanılır.

Proje şablonlarının çoğunda bir kutuyu işaretleyerek Docker desteğini etkinleştirmeyi de seçebileceğinizi unutmayın. Kimlik Doğrulamayı Değiştir düğmesini tıklatarak kimlik doğrulama desteği de ekleyebilirsiniz. Buradan seçim yapabilirsiniz:

- Kimlik doğrulama yok.
- Bireysel Kullanıcı Hesapları. Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
- İş veya Okul Hesapları. Bu seçenek, kimlik doğrulaması için Etkin Dizin, Azure AD veya Office 365'i kullanır.
- Windows Kimlik Doğrulama. Intranet uygulamaları için uygundur.

Kimlik Doğrulama olmadan standart Web Uygulaması şablonunu seçin ve **Oluştur'u**tıklatın.

![Visual Studio 2019 Temel Proje Seçenekleri ASP.NET seçin](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, ilk ASP.NET Core projeniz hakkında daha fazla bilgi edineceksiniz.

[Öğretici: İlk ASP.NET Çekirdek Web Uygulaması Oluşturma](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: C# ve ASP.NET Core ile başlayın](tutorial-aspnet-core.md) Video İzni olmadan daha ayrıntılı bir öğretici
