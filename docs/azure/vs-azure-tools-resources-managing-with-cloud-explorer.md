---
title: Bulut Gezgini ile Azure kaynaklarını yönetme | Microsoft Docs
description: Visual Studio 'da Azure kaynaklarını taramak ve yönetmek için Cloud Explorer 'ı nasıl kullanacağınızı öğrenin.
author: ghogen
manager: jillfra
assetId: 6347dc53-f497-49d5-b29b-e8b9f0e939d7
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/25/2017
ms.author: ghogen
ms.openlocfilehash: 12c82cca6c8873facc1a16a926d90fd0f3918c07
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399396"
---
# <a name="manage-the-resources-associated-with-your-azure-accounts-in-visual-studio-cloud-explorer"></a>Visual Studio Cloud Explorer'da Azure hizmetlerinizle ilişkilendirilmiş kaynakları yönetme

Cloud Explorer, Azure kaynaklarınızı ve Kaynak gruplarınızı görüntülemenize, özelliklerini incelemenize ve Visual Studio içinden önemli geliştirici tanılama eylemleri gerçekleştirmenize olanak sağlar.

[Azure Portal](https://portal.azure.com)gibi, bulut Gezgini Azure Resource Manager yığınında oluşturulmuştur. Bu nedenle, Cloud Explorer, Azure Kaynak grupları ve Logic Apps ve API uygulamaları gibi Azure hizmetleri gibi kaynakları anlamıştır ve [rol tabanlı erişim denetimini](/azure/role-based-access-control/role-assignments-portal) (RBAC) destekler.

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio 2017 veya üzeri (bkz. [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads)) seçili **Azure iş yükü** . Visual Studio 'nun önceki bir sürümünü [.NET için Microsoft Azure SDK 2,9](https://www.microsoft.com/download/details.aspx?id=51657)ile de kullanabilirsiniz.
* Microsoft Azure hesabı-hesabınız yoksa, [ücretsiz deneme için kaydolabilir](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) veya [Visual Studio abone avantajlarınızı etkinleştirebilirsiniz](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

> [!NOTE]
> Cloud Explorer 'ı görüntülemek için, **Ctrl** + arama kutusunu etkinleştirmek üzere CTRL **Q** tuşlarına basın ve ardından **bulut Gezgini** ' ni girin.

## <a name="add-an-azure-account-to-cloud-explorer"></a>Bulut Gezgini 'ne bir Azure hesabı ekleme

Bir Azure hesabıyla ilişkili kaynakları görüntülemek için öncelikle hesabı **Cloud Explorer** 'a eklemeniz gerekir.

1. **Cloud Explorer** 'Da **Hesap yönetimi** düğmesini seçin.

   ![Cloud Explorer Azure hesap ayarları simgesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. **Hesapları Yönet** ' i seçin.

   ![Bulut Gezgini eklenti hesabı bağlantısı](./media/vs-azure-tools-resources-managing-with-cloud-explorer/manage-accounts-link.png)

1. Kaynaklarını taramak istediğiniz Azure hesabında oturum açın.

1. Bir Azure hesabında oturum açtıktan sonra, bu hesapla ilişkili abonelikler görüntülenir. Gezinmek istediğiniz hesap Aboneliklerinin onay kutularını seçin ve ardından **Uygula** ' yı seçin.

   ![Bulut Gezgini: görüntülenecek Azure aboneliklerini seçin](./media/vs-azure-tools-resources-managing-with-cloud-explorer/select-subscriptions.png)

1. Kaynakları taramak istediğiniz abonelikler seçildikten sonra, bu abonelikler ve kaynaklar **bulut Gezgini** 'nde görüntülenir.

   ![Azure hesabı için bulut Gezgini kaynak listesi](./media/vs-azure-tools-resources-managing-with-cloud-explorer/resources-listed.png)

## <a name="remove-an-azure-account-from-cloud-explorer"></a>Azure hesabını bulut Gezgini 'nden kaldırma

1. **Cloud Explorer** 'Da **Hesap yönetimi** ' ni seçin.

   ![Azure hesap ayarları](./media/vs-azure-tools-resources-managing-with-cloud-explorer/azure-account-settings.png)

1. Kaldırmak istediğiniz hesabın yanındaki **hesapları Yönet** ' i seçin.

   ![Hesabı kaldır](./media/vs-azure-tools-resources-managing-with-cloud-explorer/remove-account.png)

1. Hesabı kaldırmak için **Kaldır** ' ı seçin.

    ![Bulut Gezgini hesapları Yönet iletişim kutusu](./media/vs-azure-tools-resources-managing-with-cloud-explorer/accountmanage.PNG)

## <a name="view-resource-types-or-resource-groups"></a>Kaynak türlerini veya kaynak gruplarını görüntüleme

Azure kaynaklarınızı görüntülemek için **kaynak türlerini** veya **kaynak grupları** görünümünü seçebilirsiniz.

1. **Cloud Explorer** 'da kaynak görünümü açılır listesini seçin.

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

Ek eylemler ve özellik değerleri, Azure kaynağına göre de görünebilir. Örneğin, Web Apps ve Logic Apps Ayrıca eylemler **Içinde açılır** ve **portalda aç** ' a ek olarak **hata ayıklayıcı ekler** . Bir depolama hesabı blobu, kuyruğu veya tablosu seçtiğinizde, düzenleyicilerin açılacağı eylemler görünür. Azure uygulamalarının **URL** ve **durum** özellikleri vardır, ancak depolama kaynaklarında anahtar ve bağlantı dizesi özellikleri vardır.

## <a name="find-resources-in-cloud-explorer"></a>Bulut Gezgininde kaynakları bulma

Azure hesap aboneliklerinizde belirli bir ada sahip kaynakları bulmak için, **Cloud Explorer** 'daki **arama** kutusuna adı girin.

  ![Bulut Gezgininde kaynakları bulma](./media/vs-azure-tools-resources-managing-with-cloud-explorer/search-for-resources.png)

**Arama** kutusuna karakterler girerken, kaynak ağacında yalnızca bu karakterlerle eşleşen kaynaklar görünür.
