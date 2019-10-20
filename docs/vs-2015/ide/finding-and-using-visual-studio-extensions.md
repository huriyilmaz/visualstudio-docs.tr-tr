---
title: Uzantıları bulma ve kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655873"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Visual Studio Uzantıları’nı bulma ve kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio uzantıları, Visual Studio içinde çalışan ve yeni veya geliştirilmiş Visual Studio özellikleri sağlayan kod paketlerdir. Visual Studio uzantıları hakkında daha fazla bilgiyi buradan edinebilirsiniz: [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

 **Uzantılar ve güncelleştirmeler** iletişim kutusunu, Web sitelerinden ve diğer konumlardan Visual Studio uzantıları ve örnekleri yüklemek ve sonra etkinleştirebilir, devre dışı bırakmak, güncelleştirmek veya kaldırmak için kullanabilirsiniz. (**Araçlar/Uzantılar ve güncelleştirmeler**veya **Hızlı başlatma** penceresinde tür **uzantıları** ). İletişim kutusu ayrıca yüklü örnekler ve uzantılar için güncelleştirmeleri gösterir. Ayrıca, Web sitelerinden uzantıları indirebilir veya diğer geliştiricilerden edinebilirsiniz.

> [!NOTE]
> Visual Studio 2015 ' den itibaren, Visual Studio Galerisinde barındırılan uzantılar otomatik olarak güncelleştirilir.  Bu ayarı **Uzantılar ve güncelleştirmeler** iletişim kutusu aracılığıyla değiştirebilirsiniz.  Ayrıntılar için aşağıdaki **Otomatik uzantı güncelleştirmeleri** bölümüne bakın.

## <a name="finding-visual-studio-extensions"></a>Visual Studio uzantılarını bulma
 Uzantıları, Microsoft Web sitesindeki [Visual Studio Market](https://marketplace.visualstudio.com/) veya [örnek Galerisi](https://code.msdn.microsoft.com/vstudio) ' nden yükleyebilirsiniz. Uzantılar; denetimler, örnekler, şablonlar, araçlar veya Visual Studio'ya işlevsellik katan diğer bileşenler olabilir. Visual Studio, VSıX paket biçimindeki uzantıları destekler; bunlar arasında proje şablonları, öğe şablonları, **araç kutusu** öğeleri, yönetilen uzantı ÇERÇEVESI (MEF) bileşenleri ve VSPackages bulunur. MSI tabanlı uzantıları da indirebilir ve yükleyebilirsiniz, ancak **Uzantılar ve güncelleştirmeler** iletişim kutusu bunları etkinleştiremez veya devre dışı bırakabilirler. Visual Studio Galerisi hem VSıX hem de MSI uzantılarını içerir.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Visual Studio uzantılarını yükleme veya kaldırma
 **Uzantılar ve güncelleştirmeler**' de, yüklemek istediğiniz uzantıyı bulun. (Uzantının adının adını veya parçasını biliyorsanız, **Visual Studio Galerisi** penceresinde arama yapabilirsiniz.) **İndir**ve **Yükle**' ye tıklayın. Uzantıyı yüklemek için Visual Studio 'Yu yeniden başlatmanız gerekir.

 Bağımlılıkları olan bir uzantıyı yüklemeye çalışırsanız, yükleyici bunların yüklenmiş olup olmadığını denetler. Yüklü değilse, **Uzantılar ve güncelleştirmeler** iletişim kutusu, uzantıyı yükleyebilmeniz için yüklenmesi gereken bağımlılıkları listeler.

 Bir uzantıyı kullanmayı bırakmak isterseniz devre dışı bırakabilir veya kaldırabilirsiniz. Bir uzantı devre dışı bırakıldığında yüklü kalır, ancak etkin değildir. Yalnızca VSıX uzantılarını devre dışı bırakabilirsiniz; MSI kullanılarak yüklenen uzantılar yalnızca kaldırılabilir. Uzantıyı bulun ve **Kaldır** veya **devre dışı bırak**' a tıklayın. Devre dışı bırakılmış bir uzantıyı kaldırmak için Visual Studio 'Yu yeniden başlatmanız gerekir.

## <a name="per-user-and-administrative-extensions"></a>Kullanıcı Başına ve Yönetim Uzantıları
 Çoğu uzantı Kullanıcı başına uzantılardır ve **%LocalAppData%\microsoft\visualstudio \\ < Visual Studio sürümü \> \Extensions \\** klasörüne yüklenir. Birkaç uzantı yönetim uzantılarıdır ve **\<Visual Studio yükleme klasörü > \Common7\IDE\Extensions \\** klasörüne yüklenir.

 Sisteminizi hatalar veya kötü amaçlı kod içerebilen uzantılara karşı korumak için, Kullanıcı başına uzantıları yalnızca Visual Studio normal Kullanıcı izinleriyle çalıştırıldığında yüklenecek şekilde kısıtlayabilirsiniz. Bu, Visual Studio Yönetici Kullanıcı izinleriyle çalıştırıldığında kullanıcı başına uzantıların devre dışı bırakıldığı anlamına gelir. Bunu yapmak için, **Uzantılar ve güncelleştirmeler** Seçenekler sayfasına gidin (**Araçlar/Seçenekler**, **ortam**, **Uzantılar ve güncelleştirmeler**veya **Hızlı başlatma** penceresinde yalnızca **uzantı** yazın). **Yönetici olarak çalışırken Kullanıcı Uzantıları başına yükle** onay kutusunu temizleyin ve ardından Visual Studio 'yu yeniden başlatın.

## <a name="automatic-extension-updates"></a>Otomatik uzantı güncelleştirmeleri
 Visual Studio Galerisinde yeni bir sürüm kullanılabilir olduğunda, Kullanıcı başına uzantılar otomatik olarak güncelleştirilir.  Uzantının yeni sürümü algılanır ve arka planda yüklenir ve Visual Studio 'nun bir sonraki yeniden başlatıldığında, uzantının yeni sürümü çalışıyor olur.

 Yalnızca Kullanıcı başına uzantılar otomatik olarak güncelleştirilir.  Tüm kullanıcılar için yüklenen yönetim uzantıları güncelleştirilmeyecek ve **Uzantılar ve güncelleştirmeler** Iletişim kutusu **güncelleştirmeleri** düğümü aracılığıyla yine de yeni sürümleri el ile yükleyeceksiniz. **Uzantılar ve güncelleştirmeler** iletişim kutusunun uzantısının Ayrıntılar bölmesinde hangi uzantıların otomatik olarak güncelleştirileceğini görebilirsiniz.

 Otomatik güncelleştirmeleri devre dışı bırakmak istiyorsanız, tüm uzantılara veya yalnızca belirli uzantılara yönelik özelliği devre dışı bırakabilirsiniz.

- Tüm uzantılar için otomatik güncelleştirmeleri devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** Iletişim kutusundaki **uzantılarınızı ve güncelleştirme ayarlarını değiştirin** bağlantısına tıklayın ve **uzantıları otomatik olarak güncelleştir**' in işaretini kaldırın.

- Belirli bir uzantının otomatik güncelleştirmelerini devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** iletişim kutusunun sağ tarafındaki uzantının Ayrıntılar bölmesinde **Bu uzantıyı otomatik olarak güncelleştir** seçeneğinin işaretini kaldırın.

> [!NOTE]
> Visual Studio 2015 güncelleştirme 2 ' den başlayarak, Kullanıcı başına uzantılar, tüm Kullanıcı Uzantıları veya her ikisi için de otomatik güncelleştirme isteyip istemediğinizi ( **Araçlar/Seçenekler/ortam/Uzantılar ve güncelleştirmeler**içinde) belirtebilirsiniz (varsayılan ayar).

## <a name="sample-master-copies-and-working-copies"></a>Örnek ana kopyalar ve çalışma kopyaları
 Çevrimiçi bir örneği yüklediğinizde, çözüm iki konumda depolanır:

- Çalışma kopyası, **Yeni proje** iletişim kutusunda belirttiğiniz konumda depolanır.

- Ayrı bir ana kopya bilgisayarınızda depolanır.

  Bu örneklerle ilgili görevleri gerçekleştirmek için **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanabilirsiniz:

- Yüklediğiniz örneklerin ana kopyalarını listeleyin.

- Bir örneğin ana kopyasını devre dışı bırakın veya kaldırın.

- Örnek Paketleri (bir teknoloji veya özellik ile ilgili örnek koleksiyonları) yükleyin.

- Tek tek çevrimiçi örnekleri yükleyin. (Bunu **Yeni proje** iletişim kutusunda da yapabilirsiniz.)

- Yüklü örnekler için kaynak kodu değişiklikleri yayımlandığında güncelleştirme bildirimlerini görüntüleyin.

- Bir güncelleştirme bildirimi olduğunda, yüklü bir örneğin ana kopyasını güncelleştirin.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Uzantılar ve Güncelleştirmeler İletişim Kutusunu Kullanmadan Yükleme
 .vsix dosyalarında paketlenmiş uzantılar Visual Studio Galerisi dışındaki konumlarda bulunabilir. **Uzantılar ve güncelleştirmeler** iletişim kutusu bu dosyaları algılayamaz, ancak dosyayı çift tıklayarak veya dosyayı seçip ENTER tuşuna basarak bir. vsix dosyası yükleyebilirsiniz. Bundan sonra yönergeleri izlemeniz yeterlidir. Uzantı yüklendiğinde, uzantıyı etkinleştirmek, devre dışı bırakmak veya kaldırmak için **Uzantılar ve güncelleştirmeler** iletişim kutusunu kullanabilirsiniz.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Uzantılar ve güncelleştirmeler Iletişim kutusu tarafından desteklenmeyen uzantı türleri
 Visual Studio, Microsoft yükleyicisi (MSI) tarafından yüklenen, ancak **Uzantılar ve güncelleştirmeler** iletişim kutusunda değişiklik yapılmadan yüklenmeyen uzantıları desteklemeye devam etmektedir.

> [!TIP]
> MSI tabanlı bir uzantı. valtmanifest dosyası uzantısı içeriyorsa, uzantı **Uzantılar ve güncelleştirmeler** iletişim kutusunda görünür.
