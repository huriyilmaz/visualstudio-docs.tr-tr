---
description: Visual Studio 2019 sürüm 16,8 ' den başlayarak, Visual Studio 'dan ClickOnce kullanarak .NET Core 3,1 veya daha yeni, Windows Masaüstü uygulamaları yayımlamak için Yayımla aracını kullanabilirsiniz.
title: ClickOnce kullanarak .NET Windows masaüstü uygulaması dağıtma
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165715"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>ClickOnce kullanarak .NET Windows masaüstü uygulaması dağıtma

Visual Studio 2019 sürüm 16,8 ' den başlayarak, Visual Studio 'dan ClickOnce kullanarak .NET Core 3,1 veya daha yeni, Windows Masaüstü uygulamaları yayımlamak için **Yayımla** aracını kullanabilirsiniz.

> [!NOTE]
> .NET Framework bir Windows uygulaması yayımlamanız gerekiyorsa bkz. [ClickOnce kullanarak masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# veya Visual Basic).

## <a name="publishing-with-clickonce"></a>ClickOnce ile yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla** ' yı seçin (veya **Yapı**  >  **Yayımla** menü öğesini kullanın).

    ![Çözüm Gezgini içindeki proje bağlam menüsündeki Yayımla komutu](../deployment/media/quickstart-clickonce-solution-explorer.png "Yayımla ' yı seçin")

1. Daha önce herhangi bir yayımlama profili yapılandırdıysanız **Yayımla** sayfası görüntülenir. **Yeni**'yi seçin.

1. **Yayımla** sihirbazında **klasör**' ü seçin.

    ![Yayımla hedefi olarak klasör seçin](../deployment/media/quickstart-clickonce-publish-folder-category.png "Klasör Seç")

1. **Belirli hedef** sayfasında, **ClickOnce**' ı seçin.

    ![Belirli hedef olarak ClickOnce seçin](../deployment/media/quickstart-clickonce-publish-folder-target.png "ClickOnce seçin")

1. Yayımlama konumunu seçmek için bir yol girin veya **bul** ' u seçin.

    ![Yayımlama konumu için yolu belirtin](../deployment/media/quickstart-clickonce-publish-location.png "Bir yol girin")

1. **Konum yüklemeyi** , kullanıcıların uygulamayı nereden yükleyeceğini seçin.

    ![Klasörün yolunu belirtin](../deployment/media/quickstart-clickonce-install-location.png "Yüklemesi konumunu seçin")

1. **Ayarlar** sayfasında, ClickOnce için gerekli ayarları sağlayabilirsiniz.

1. Bir UNC yolundan veya Web sitesinden yüklemeyi seçtiyseniz, Bu sayfa uygulamanın çevrimdışı kullanılabilir olup olmadığını belirtmenizi sağlar. Seçildiğinde, bu seçenek uygulamayı kullanıcılar başlangıç menüsünde listeler ve yeni bir sürüm yayımlandığında uygulamanın otomatik olarak güncelleştirilmesini sağlar. Varsayılan olarak, güncelleştirmeleri, yüklemenin konumundan bulabilirsiniz.  Güncelleştirmeler için farklı bir konuma sahip olmak istiyorsanız, bu ayarı Güncelleştir bağlantısını kullanarak belirtebilirsiniz. Uygulamanın çevrimdışı kullanılabilir olmasını istemiyorsanız, bu, yüklemenin konumundan çalıştırılır.

    ![Yayımlama ayarlarını belirtin](../deployment/media/quickstart-clickonce-unc-settings.png "Yayımlama ayarlarını seçin")

1. Bir CD, DVD veya USB sürücüsünden yüklemeyi seçtiyseniz bu sayfa, uygulamanın otomatik güncelleştirmeleri destekleyip desteklemediğini belirtmenize de olanak tanır. Güncelleştirmeleri desteklemeyi seçerseniz, güncelleştirme konumu zorunludur ve geçerli bir UNC yolu veya Web sitesi olmalıdır.

    ![Yayımlama ayarlarını seçin](../deployment/media/quickstart-clickonce-settings.png "Yayımlama ayarlarını seçin")

Bu sayfada yer alan, kuruluma hangi **uygulama dosyalarının** ekleneceğini, hangi **Önkoşul** paketlerinin yükleneceğini ve sayfanın en üstündeki bağlantılar aracılığıyla diğer **seçenekleri** belirtmenize olanak tanır.

Ayrıca, bu sayfada yayımla sürümünü ve sürüm her bir yayınla otomatik olarak arttırılacağını da ayarlayabilirsiniz.

> [!NOTE]
> Yayımlama sürümü numarası her ClickOnce profili için benzersizdir. Daha sonra bir profile sahip olmayı planlıyorsanız bunu aklınızda tutmanız gerekir.

10. **Bildirimleri imzala** sayfasında, bildirimlerin imzalanmasını ve kullanılacak sertifikayı belirtebilirsiniz.

    ![ClickOnce bildirimlerini imzala](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. **Yapılandırma** sayfasında, istenen proje yapılandırmasını seçebilirsiniz.

     ![Yayımlama yapılandırmasını belirtin](../deployment/media/quickstart-clickonce-configuration.png)

    Hangi ayarı seçeceğiniz hakkında daha fazla yardım için aşağıdakilere bakın:

    - [Çerçeveye bağımlı ve kendinden bağımsız dağıtım](/dotnet/core/deploying/)
    - [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, et)](/dotnet/core/rid-catalog)
    - [Hata ayıklama ve sürüm yapılandırması](../ide/understanding-build-configurations.md)

1. Yeni ClickOnce yayımlama profilini kaydetmek için **son** ' u seçin.

1. **Özet** sayfasında **Yayımla** ' yı seçin ve Visual Studio projeyi oluşturur ve belirtilen Yayımla klasörüne yayımlar. Bu sayfada Ayrıca bir profil özeti gösterilir.

    ![Profil özetini gösteren özellik bölmesini Yayımla](../deployment/media/quickstart-clickonce-summary.png)

1. Yeniden yayımlamak için **Yayımla**' yı seçin.

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamaları için:

- [.NET Framework ve uygulamaları dağıtma](/dotnet/framework/deployment/)
- [ClickOnce Başvurusu](clickonce-reference.md)
