---
title: Sunucu Gezgini 'den Azure sanal makinelerine erişme | Microsoft Docs
description: Visual Studio Sunucu Gezgini Azure sanal makinelerini (VM 'Ler) oluşturma ve yönetme hakkında genel bakış alın.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 689317f3789188a4551aaee588d7f0c006bcb4f7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632997"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Sunucu Gezgini'nden Azure Sanal Makineler'e erişme

::: moniker range=">=vs-2022"
> [!Important]
> Sunucu Gezgini Azure düğümü Visual Studio 2022 ' de kullanımdan kaldırılmıştır. Azure portalını kullanabilir veya önceki Visual Studio sürümlerinde Sunucu Gezgini Azure düğümünü kullanmaya devam edebilirsiniz.
>
> ayrıca, Microsoft 'tan ücretsiz ve tek başına bir uygulama [Microsoft Azure Depolama Gezgini](/azure/vs-azure-tools-storage-manage-with-storage-explorer) . Windows, macos ve Linux 'ta Azure Depolama verileriyle görsel olarak çalışmak için bu uygulamayı kullanabilirsiniz.
>
> Visual Studio 2022 hakkında daha fazla bilgi için [sürüm notlarımıza](/visualstudio/releases/2022/release-notes-preview/)bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Azure tarafından barındırılan sanal makineleriniz varsa bunlara Sunucu Gezgini erişebilirsiniz. Mobil hizmetlerinizi görüntülemek için önce Azure aboneliğinizde oturum açmanız gerekir. oturum açmak için Sunucu Gezgini Azure düğümünün kısayol menüsünü açın ve **Microsoft Azure için Bağlan** öğesini seçin.

1. Cloud Explorer 'da bir sanal makine seçin ve ardından Özellikler penceresini göstermek için F4 tuşunu seçin.

    Aşağıdaki tabloda kullanılabilen özellikler gösterilmektedir, ancak bunların hepsi salt okunurdur. Bunları değiştirmek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | DNS Adı |Sanal makinenin Internet adresine sahip URL. |
   | Ortam |Bir sanal makine için, bu özelliğin değeri her zaman üretime yöneliktir. |
   | Name |Sanal makinenin adı. |
   | Boyut |Kullanılabilir bellek ve disk alanı miktarını yansıtan sanal makinenin boyutu. Daha fazla bilgi için bkz. [sanal makine boyutları](/azure/cloud-services/cloud-services-sizes-specs). |
   | Durum |Değerler, başlatma, başlatma, durdurma, durdurma ve durum alma içerir. Durum alma görünürse, geçerli durum bilinmiyor olur. Bu özelliğin değerleri, [Azure Portal](https://portal.azure.com)kullanılan değerlerden farklıdır. |
   | SubscriptionID |Azure hesabınızın abonelik KIMLIĞI. Bir aboneliğin özelliklerini görüntüleyerek [Azure Portal](https://portal.azure.com) bu bilgileri gösterebilirsiniz. |
2. Bir uç nokta düğümü seçin ve ardından **Özellikler** penceresini görüntüleyin.
3. Aşağıdaki tabloda, uç noktaların kullanılabilir özellikleri açıklanmıştır, ancak bunlar salt okunurdur. Bir sanal makineye yönelik uç noktaları eklemek veya düzenlemek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | Ad |Uç nokta için bir tanımlayıcı. |
   | Özel bağlantı noktası |Uygulamanıza iç ağ erişimi için bağlantı noktası. |
   | Protokol |Bu uç noktanın aktarım katmanının, TCP veya UDP kullandığı protokol. |
   | Genel Bağlantı Noktası |Uygulamanıza genel erişim için kullanılan bağlantı noktası. |

::: moniker-end