---
title: Bulut Gezgini ile Azure kaynaklarını yönetme | Microsoft Docs
description: Visual Studio içindeki Azure kaynaklarını taramak ve yönetmek için Cloud Explorer 'ı nasıl kullanacağınızı öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: e8ac1d909cba36a7204ae781aacf1b8fdb2abee0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098586"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio Cloud Explorer'da Azure hizmetlerinizle ilişkilendirilmiş kaynakları yönetme

::: moniker range=">=vs-2022"
> [!Important]
> bulut gezgini Visual Studio 2022 ' de kullanımdan kaldırılmıştır. Bunun yerine, aşağıdaki alternatifleri kullanabilirsiniz:
> - [Microsoft Azure Depolama Gezgini](/azure/vs-azure-tools-storage-manage-with-storage-explorer) , Microsoft 'tan ücretsiz ve tek başına bir uygulamadır. Windows, macos ve Linux 'ta Azure Depolama verileriyle görsel olarak çalışmak için bu uygulamayı kullanabilirsiniz.
> - [Kudu konsolu](https://github.com/projectkudu/kudu/wiki/Kudu-console) , App Service sunucusuna ve dosya sistemine doğrudan, yükseltilmiş komut satırı erişimi sağlar. Bu, her ikisi de değerli bir hata ayıklama aracıdır ve paketleri yükleme gibi CLı işlemlerine izin verir.
>
> Gerekirse, Azure portalını kullanabilir veya önceki Visual Studio sürümlerinde Sunucu Gezgini Azure düğümünü kullanmaya devam edebilirsiniz.
>
> Visual Studio 2022 hakkında daha fazla bilgi için [sürüm notlarımıza](/visualstudio/releases/2022/release-notes-preview/)bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Cloud Explorer, Azure kaynaklarınızı ve Kaynak gruplarınızı görüntülemenize, özelliklerini incelemenize ve Visual Studio içinden önemli geliştirici tanılama eylemleri gerçekleştirmenize olanak sağlar.

[Azure Portal](https://portal.azure.com)gibi, bulut Gezgini Azure Resource Manager yığınında oluşturulmuştur. Bu nedenle, Cloud Explorer, Azure Kaynak grupları ve Logic Apps ve API uygulamaları gibi Azure hizmetleri gibi kaynakları anlamıştır ve [rol tabanlı erişim denetimini](/azure/role-based-access-control/role-assignments-portal) (RBAC) destekler.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 veya üzeri (bkz. [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads)) seçili **Azure iş yükü** . daha önceki bir Visual Studio sürümünü [.NET için Microsoft Azure SDK 2,9](https://www.microsoft.com/download/details.aspx?id=51657)ile de kullanabilirsiniz.
* Microsoft Azure hesabı-hesabınız yoksa, [ücretsiz deneme için kaydolabilir](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) veya [Visual Studio abone avantajlarınızı etkinleştirebilirsiniz](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

> [!NOTE]
> Cloud Explorer 'ı görüntülemek için,  + arama kutusunu etkinleştirmek üzere CTRL **Q** tuşlarına basın ve ardından **bulut Gezgini**' ni girin.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Bulut Gezgini 'ne bir Azure hesabı ekleme

Bir Azure hesabıyla ilişkili kaynakları görüntülemek için öncelikle hesabı **Cloud Explorer**'a eklemeniz gerekir.

1. **Cloud Explorer**'Da **Hesap yönetimi** düğmesini seçin.

   ![Cloud Explorer Azure hesap ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. **Hesapları Yönet**' i seçin.

   ![Bulut Gezgini eklenti hesabı bağlantısı](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Kaynaklarını taramak istediğiniz Azure hesabında oturum açın.

1. Bir Azure hesabında oturum açtıktan sonra, bu hesapla ilişkili abonelikler görüntülenir. Gezinmek istediğiniz hesap Aboneliklerinin onay kutularını seçin ve ardından **Uygula**' yı seçin.

   ![Bulut Gezgini: görüntülenecek Azure aboneliklerini seçin](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Kaynakları taramak istediğiniz abonelikler seçildikten sonra, bu abonelikler ve kaynaklar **bulut Gezgini**'nde görüntülenir.

   ![Azure hesabı için bulut Gezgini kaynak listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Azure hesabını bulut Gezgini 'nden kaldırma

1. **Cloud Explorer**'Da **Hesap yönetimi**' ni seçin.

   ![Azure hesap ayarları](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Kaldırmak istediğiniz hesabın yanındaki **hesapları Yönet**' i seçin.

   ![Hesabı kaldır](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Hesabı kaldırmak için **Kaldır** ' ı seçin.

    ![Bulut Gezgini hesapları Yönet iletişim kutusu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Kaynak türlerini veya kaynak gruplarını görüntüleme

Azure kaynaklarınızı görüntülemek için **kaynak türlerini** veya **kaynak grupları** görünümünü seçebilirsiniz.

1. **Cloud Explorer**'da kaynak görünümü açılır listesini seçin.

   ![İstenen kaynak görünümünü seçmek için bulut Gezgini açılan listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-view-dropdown.png)

1. Bağlam menüsünde istediğiniz görünümü seçin:

   * **Kaynak türleri** görünümü- [Azure Portal](https://portal.azure.com)kullanılan ortak görünüm, Azure kaynaklarınızı Web Apps, depolama hesapları ve sanal makineler gibi türlerine göre kategorilere ayırarak gösterir.
   * **Kaynak grupları** görünümü-Azure kaynaklarını Ilişkili oldukları Azure Kaynak grubuna göre kategorilere ayırır. Kaynak grubu, genellikle belirli bir uygulama tarafından kullanılan Azure kaynakları grubudur. Azure Kaynak grupları hakkında daha fazla bilgi edinmek için bkz. [Azure Resource Manager genel bakış](/azure/azure-resource-manager/resource-group-overview).

   Aşağıdaki görüntüde, iki kaynak görünümünün karşılaştırması gösterilmektedir:

   ![Bulut Gezgini kaynak görünümleri karşılaştırması](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resource-views-comparison.png)

## <a name="view-and-navigate-resources-in-cloud-explorer"></a>Cloud Explorer 'da kaynakları görüntüleme ve gezinme

Bir Azure kaynağına gitmek ve bu bilgileri Cloud Explorer 'da görüntülemek için, öğenin türünü veya ilişkili kaynak grubunu genişletin ve ardından kaynağı seçin. Bir kaynak seçtiğinizde, bulut Gezgini 'nin altındaki iki sekmede ( **Eylemler** ve **Özellikler** ) bilgi görüntülenir.

* **Eylemler** sekmesi-seçili kaynak Için Cloud Explorer 'da gerçekleştirebileceğiniz eylemleri listeler. Bu seçenekleri, bağlam menüsünü görüntülemek için kaynağa sağ tıklayarak da görüntüleyebilirsiniz.

* **Özellikler** sekmesi-kaynağın türü, yerel ayarı ve ilişkilendirildiği kaynak grubu gibi özelliklerini gösterir.

Aşağıdaki görüntüde App Service için her sekmede gördüklerinize ilişkin örnek bir karşılaştırma gösterilmektedir:

  ![Cloud Explorer 'ın ekran görüntüsü](./media/vs-azure-tools-resources-managing-with-cloud-explorer/actions-and-properties.png)

Her kaynak, **portalda açık** olan eylemi içerir. Bu eylemi seçtiğinizde, Cloud Explorer [Azure Portal](https://portal.azure.com)seçili kaynağı görüntüler. **Portal 'Da aç** özelliği, derin iç içe geçmiş kaynaklara gitmek için kullanışlıdır.

Ek eylemler ve özellik değerleri, Azure kaynağına göre de görünebilir. Örneğin, Web Apps ve Logic Apps Ayrıca eylemler **Içinde açılır** ve **portalda aç**' a ek olarak **hata ayıklayıcı ekler** . Bir depolama hesabı blobu, kuyruğu veya tablosu seçtiğinizde, düzenleyicilerin açılacağı eylemler görünür. Azure uygulamalarının **URL** ve **durum** özellikleri vardır, ancak depolama kaynaklarında anahtar ve bağlantı dizesi özellikleri vardır.

## <a name="find-resources-in-cloud-explorer"></a>Bulut Gezgininde kaynakları bulma

Azure hesap aboneliklerinizde belirli bir ada sahip kaynakları bulmak için, **Cloud Explorer**'daki **arama** kutusuna adı girin.

  ![Bulut Gezgininde kaynakları bulma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

**Arama** kutusuna karakterler girerken, kaynak ağacında yalnızca bu karakterlerle eşleşen kaynaklar görünür.

::: moniker-end
