---
title: Azure Sanal Makineler'e Sunucu Gezgini | Microsoft Docs
description: Sanal makinelerde Azure sanal makinelerinin (VM) nasıl oluşturularak yönetildiklerinin nasıl görüntü Sunucu Gezgini genel Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: ab67a81d761f2e17c82b75fb59a201188cf80986
ms.sourcegitcommit: b770b99034e65c91b29bea87bc6f5fa02348515b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112997637"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Sunucu Gezgini'nden Azure Sanal Makineler'e erişme

::: moniker range=">=vs-2022"
> [!Important]
> Sunucu Gezgini Azure düğümü, 2022'Visual Studio kullanımdan kaldırıldı. Azure Portalı'nın önceki sürümlerinde azure portalını kullanabilir veya Sunucu Gezgini Azure düğümünü kullanmaya Visual Studio.
>
> Ayrıca [Microsoft Azure Depolama Gezgini,](/azure/vs-azure-tools-storage-manage-with-storage-explorer) Microsoft'un ücretsiz ve tek başına uygulamasıdır. Windows, macOS ve Linux'ta Azure Depolama verileriyle görsel olarak çalışmak için bunu kullanabilirsiniz.
>
> 2022'Visual Studio daha fazla bilgi için sürüm [notlarımıza bakın.](/visualstudio/releases/2022/release-notes-preview/)

::: moniker-end

::: moniker range="<=vs-2017"

Azure tarafından barındırılan sanal makineleriniz varsa, sanal makinelere sanal makine Sunucu Gezgini. Mobil hizmetlerinizi görüntülemek için önce Azure aboneliğinde oturum açmanız gerekir. Oturum açmak için, azure düğümü için kısayol menüsünü Sunucu Gezgini ve **Microsoft Azure.**

1. Bulut Gezgini'nde bir sanal makine seçin ve ardından F4 anahtarını seçarak özellikler penceresini açın.

    Aşağıdaki tabloda hangi özelliklerin kullanılabilir olduğu, ancak bunların hepsi salt okunurdur. Bunları değiştirmek için [Azure portal.](https://portal.azure.com)

   | Özellik | Açıklama |
   | --- | --- |
   | DNS Adı |Sanal makinenin İnternet adresine sahip URL. |
   | Ortam |Bir sanal makine için bu özelliğin değeri her zaman Üretim olur. |
   | Name |Sanal makinenin adı. |
   | Boyut |Kullanılabilir bellek ve disk alanı miktarını yansıtan sanal makinenin boyutu. Daha fazla bilgi için [bkz. Sanal Makine Boyutları.](/azure/cloud-services/cloud-services-sizes-specs) |
   | Durum |Değerler Başlangıç, Başlatıldı, Durduruluyor, Durduruldu ve Durumu Alma'dır. Alma Durumu görüntülenirse, geçerli durum bilinmiyor. Bu özelliğin değerleri, üzerinde kullanılan değerlerden [Azure portal.](https://portal.azure.com) |
   | SubscriptionID |Azure hesabınız için abonelik kimliği. Bir aboneliğin özelliklerini görüntü [Azure portal](https://portal.azure.com) bu bilgileri abonelikte gösterebilirsiniz. |
2. Bir uç nokta düğümü seçin ve özellikler **penceresini** açın.
3. Aşağıdaki tabloda uç noktaların kullanılabilir özellikleri açıklasa da bunlar salt okunurdur. Bir sanal makinenin uç noktalarını eklemek veya düzenlemek için [Azure portal.](https://portal.azure.com)

   | Özellik | Açıklama |
   | --- | --- |
   | Ad |Uç noktanın tanımlayıcısı. |
   | Özel Bağlantı Noktası |Uygulamanıza dahili ağ erişimi için bağlantı noktası. |
   | Protokol |Bu uç nokta için aktarım katmanının kullandığı protokol, TCP veya UDP. |
   | Genel Bağlantı Noktası |Uygulamanıza genel erişim için kullanılan bağlantı noktası. |

::: moniker-end