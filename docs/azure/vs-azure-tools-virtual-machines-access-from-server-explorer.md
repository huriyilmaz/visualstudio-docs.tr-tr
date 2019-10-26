---
title: Sunucu Gezgini 'den Azure sanal makinelerine erişme | Microsoft Docs
description: Visual Studio 'da Sunucu Gezgini Azure sanal makinelerini (VM 'Ler) oluşturma ve yönetme hakkında genel bakış alın.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 8fd5d81e721bc2df7041d4cb724687e5ee540a7f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911665"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Sunucu Gezgini'nden Azure Sanal Makineler'e erişme

Azure tarafından barındırılan sanal makineleriniz varsa bunlara Sunucu Gezgini erişebilirsiniz. Mobil hizmetlerinizi görüntülemek için önce Azure aboneliğinizde oturum açmanız gerekir. Oturum açmak için Sunucu Gezgini Azure düğümünün kısayol menüsünü açın ve **Microsoft Azure Bağlan**' ı seçin.

1. Cloud Explorer 'da bir sanal makine seçin ve ardından Özellikler penceresini göstermek için F4 tuşunu seçin.

    Aşağıdaki tabloda kullanılabilen özellikler gösterilmektedir, ancak bunların hepsi salt okunurdur. Bunları değiştirmek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | DNS adı |Sanal makinenin Internet adresine sahip URL. |
   | Ortam |Bir sanal makine için, bu özelliğin değeri her zaman üretime yöneliktir. |
   | Name |Sanal makinenin adı. |
   | Boyut |Kullanılabilir bellek ve disk alanı miktarını yansıtan sanal makinenin boyutu. Daha fazla bilgi için bkz. [sanal makine boyutları](/azure/cloud-services/cloud-services-sizes-specs). |
   | Durum |Değerler, başlatma, başlatma, durdurma, durdurma ve durum alma içerir. Durum alma görünürse, geçerli durum bilinmiyor olur. Bu özelliğin değerleri, [Azure Portal](https://portal.azure.com)kullanılan değerlerden farklıdır. |
   | SubscriptionID |Azure hesabınızın abonelik KIMLIĞI. Bir aboneliğin özelliklerini görüntüleyerek [Azure Portal](https://portal.azure.com) bu bilgileri gösterebilirsiniz. |
2. Bir uç nokta düğümü seçin ve ardından **Özellikler** penceresini görüntüleyin.
3. Aşağıdaki tabloda, uç noktaların kullanılabilir özellikleri açıklanmıştır, ancak bunlar salt okunurdur. Bir sanal makineye yönelik uç noktaları eklemek veya düzenlemek için [Azure Portal](https://portal.azure.com)kullanın.

   | Özellik | Açıklama |
   | --- | --- |
   | Name |Uç nokta için bir tanımlayıcı. |
   | Özel bağlantı noktası |Uygulamanıza iç ağ erişimi için bağlantı noktası. |
   | Protokol |Bu uç noktanın aktarım katmanının, TCP veya UDP kullandığı protokol. |
   | Genel bağlantı noktası |Uygulamanıza genel erişim için kullanılan bağlantı noktası. |
