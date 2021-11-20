---
title: Cloud Explorer ile Azure kaynaklarını | Microsoft Docs
description: Bulut Gezgini'ni kullanarak bulut gezgininin içindeki Azure kaynaklarına göz atabilir ve Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: bd80d022a71e1c5a13d084c477458537bc2330b6
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132879803"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio Cloud Explorer'da Azure hizmetlerinizle ilişkilendirilmiş kaynakları yönetme

::: moniker range=">=vs-2022"
> [!Important]
> Cloud Explorer, 2022'Visual Studio kaldırıldı. Bunun yerine aşağıdaki alternatifleri kullanabilirsiniz:
> - [Microsoft Microsoft Azure Depolama Gezgini](/azure/vs-azure-tools-storage-manage-with-storage-explorer) ücretsiz ve tek başına bir uygulama olan bu uygulamayı kullanın. Azure, macOS ve Linux'ta azure Depolama verileriyle görsel Windows için kullanabilirsiniz.
> - Azure İşlevi uygulamasında Azure App Service ayıklamak için Bağlı Hizmetler'i veya tüm projelerde kullanılabilen Yayımla özelliğini kullanabilirsiniz. Yayımlama için Visual Studio bağlıysanız, bu seçenek barındırma bölümündeki ek seçenekler altında kullanılabilir. Yayımlama özelliğini kullanamıyorsanız, Bağlı Hizmet sekmesinden herhangi bir Azure App Service veya Azure İşlevi uygulamasına bağlanabilir ve uzaktan hata ayıklama, uzak profil, siteyi başlatma/durdurma, akış günlüklerini görüntüleme gibi çeşitli işlemleri çağırabilirsiniz. 
> - [Kudu konsolu,](https://github.com/projectkudu/kudu/wiki/Kudu-console) App Service sunucusuna ve dosya sistemine doğrudan, yükseltilmiş komut satırı erişimi verir. Bu hem değerli bir hata ayıklama aracıdır hem de paketleri yükleme gibi CLI işlemlerine olanak sağlar.
>
> Gerekirse, Azure Portalını kullanabilir veya önceki sürümlerde Sunucu Gezgini Azure düğümünü kullanmaya Visual Studio.
>
> 2022'Visual Studio daha fazla bilgi için sürüm [notlarımıza bakın.](/visualstudio/releases/2022/release-notes/)

::: moniker-end

::: moniker range="<=vs-2019"

Bulut Gezgini, Azure kaynaklarınızı ve kaynak gruplarınızı görüntülemenizi, özelliklerini incelemenizi ve uygulamanın içindeki önemli geliştirici tanılama eylemlerini Visual Studio.

Bulut [gezgini Azure portal](https://portal.azure.com)gibi, Bulut Gezgini de Azure Resource Manager yerleşiktir. Bu nedenle, Cloud Explorer Azure kaynak grupları ve Logic Apps ve API uygulamaları [](/azure/role-based-access-control/role-assignments-portal) gibi Azure hizmetleri gibi kaynakları anlar ve rol tabanlı erişim denetimi (RBAC) desteği sunar.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio iş yükü seçiliyken 2017 [veya sonraki](https://visualstudio.microsoft.com/downloads)bir Visual Studio (bkz. **indirmeler)** . 2.9 sürümüyle Visual Studio önceki bir .NET için Microsoft Azure SDK da kullanabilirsiniz.
* Microsoft Azure hesabı - Hesabınız yoksa ücretsiz deneme sürümüne [](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) kaydolabilirsiniz veya abone avantajlarınızı [Visual Studio etkinleştirebilirsiniz.](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)

> [!NOTE]
> Cloud Explorer'ı görüntülemek için **Ctrl** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve Cloud **Explorer yazın.**

## <a name="add-an-azure-account-to-cloud-explorer"></a>Bulut Gezgini'ne Azure hesabı ekleme

Bir Azure hesabıyla ilişkili kaynakları görüntülemek için öncelikle hesabı Cloud **Explorer'a eklemeniz gerekir.**

1. Bulut **Gezgini'nde** Hesap Yönetimi **düğmesini** seçin.

   ![Cloud Explorer Azure hesabı ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Hesapları **yönet'i seçin.**

   ![Cloud Explorer hesap ekle bağlantısı](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Kaynaklarına göz atmak istediğiniz Azure hesabında oturum açın.

1. Azure hesabında oturum açtıktan sonra bu hesapla ilişkili abonelikler görüntülenir. Göz atmak istediğiniz hesap abonelikleri için onay kutularını seçin ve uygula'ya **tıklayın.**

   ![Bulut Gezgini: Görüntülemek için Azure aboneliklerini seçin](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Kaynaklarına göz atmak istediğiniz abonelikleri seçdikten sonra, bu abonelikler ve kaynaklar Bulut **Gezgini'nde görüntülenir.**

   ![Azure hesabı için Cloud Explorer kaynak listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Azure hesabını Cloud Explorer'dan kaldırma

1. Bulut **Gezgini'nde** Hesap **Yönetimi'ni seçin.**

   ![Azure hesap ayarları](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Kaldırmak istediğiniz hesabın yanındaki Hesapları **Yönet'i seçin.**

   ![Hesabı kaldırma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Hesabı **kaldırmak için** Kaldır'ı seçin.

    ![Cloud Explorer Hesapları yönet iletişim kutusu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Kaynak türlerini veya kaynak gruplarını görüntüleme

Azure kaynaklarınızı görüntülemek için Kaynak Türleri veya **Kaynak Grupları** **görünümünü seçebilirsiniz.**

1. Bulut **Gezgini'nde** kaynak görünümü açılan listesinden öğesini seçin.

   ![İstenen kaynaklar görünümünü seçmek için Cloud Explorer açılan listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Bağlam menüsünden istediğiniz görünümü seçin:

   * **Kaynak Türleri** görünümü - Azure portal'da kullanılan genel görünüm, Azure kaynaklarınızı web uygulamaları, depolama hesapları ve sanal makineler gibi türlerine göre kategorilere ayrılmış şekilde gösterir. [](https://portal.azure.com)
   * **Kaynak Grupları** görünümü - Azure kaynaklarını ilişkili olduğu Azure kaynak grubuna göre kategorilere ayrılmıştır. Kaynak grubu, genellikle belirli bir uygulama tarafından kullanılan bir Azure kaynakları paketidir. Azure kaynak grupları hakkında daha fazla bilgi edinmek için [bkz. Azure Resource Manager Genel Bakış.](/azure/azure-resource-manager/resource-group-overview)

   Aşağıdaki görüntüde iki kaynak görüntüsünün karşılaştırması yer alenidir:

   ![Cloud Explorer kaynak görünümlerini karşılaştırma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Bulut Gezgini'nde kaynakları görüntüleme ve gezinme

Bir Azure kaynağına gitmek ve bilgilerini Cloud Explorer'da görüntülemek için öğenin türünü veya ilişkili kaynak grubunu genişletin ve kaynağı seçin. Bir kaynak seçerek Bilgiler, Bulut Gezgini'nin  alt kısmında yer alan Eylemler ve Özellikler sekmelerinde görünür. 

* **Eylemler** sekmesi - Seçilen kaynak için Bulut Gezgini'nde gerçekleştirebilirsiniz eylemleri listeler. Bağlam menüsünü görüntülemek için kaynağa sağ tıklayarak da bu seçenekleri görüntüebilirsiniz.

* **Özellikler** sekmesi - Kaynağın türü, yereli ve ilişkili olduğu kaynak grubu gibi özelliklerini gösterir.

Aşağıdaki görüntüde, bir uygulama için her sekmede gördüğünüzlerin örnek bir karşılaştırması App Service:

  ![Bulut Gezgini'nin ekran görüntüsü](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Her kaynağın **Portalda aç eylemi vardır.** Bu eylemi seçtiğiniz zaman, Cloud Explorer seçilen kaynağı [Azure portal.](https://portal.azure.com) Portalda **aç** özelliği, iç içe geçmiş kaynaklara gezinmek için kullanışlıdır.

Azure kaynağına bağlı olarak ek eylemler ve özellik değerleri de görünebilir. Örneğin, web uygulamaları ve mantıksal uygulamalarda  Portalda  aç'a ek olarak Tarayıcıda aç ve Hata ayıklayıcı ekle **eylemleri de vardır.** Bir depolama hesabı blobu, kuyruğu veya tablosu seçtiğiniz zaman düzenleyicileri açma eylemleri görüntülenir. Azure uygulamaları **URL ve** Durum **özelliklerine** sahipken depolama kaynakları anahtar ve bağlantı dizesi özelliklerine sahiptir.

## <a name="find-resources-in-cloud-explorer"></a>Cloud Explorer'da kaynakları bulma

Azure hesabı aboneliklerinize belirli bir adla kaynakları bulmak için, Cloud **Explorer'daki Arama** kutusuna **adı girin.**

  ![Bulut Gezgini'nde kaynakları bulma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

Arama kutusuna karakterler **girerken,** kaynak ağacında yalnızca bu karakterlerle eşan kaynaklar görünür.

::: moniker-end
