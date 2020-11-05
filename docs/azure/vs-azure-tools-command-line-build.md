---
title: Azure için komut satırı derlemesi | Microsoft Docs
description: Azure için komut satırı derlemesi
author: ghogen
manager: jillfra
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: 940636c6df2f16445b5510543b5f2a39d7076f7e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398949"
---
# <a name="building-azure-projects-from-the-command-line"></a>Komut satırından Azure projeleri oluşturma
Microsoft Build Engine (MSBuild) kullanarak, Visual Studio 'Nun yüklü olmadığı derleme Laboratuvarı ortamlarında ürünler oluşturabilirsiniz. MSBuild, Microsoft tarafından genişletilebilir ve tam olarak desteklenen proje dosyaları için bir XML biçimi kullanır. MSBuild dosya biçimini kullanarak bir veya daha fazla platform ve yapılandırma için hangi öğelerin oluşturulması gerektiğini tanımlayabilirsiniz.

MSBuild 'i komut satırında de çalıştırabilirsiniz ve bu konuda bu yaklaşım açıklanır. Komut satırındaki özellikleri ayarlayarak, bir proje için özel konfigürasyonlar oluşturabilirsiniz. Benzer şekilde, MSBuild derlemesi olan hedefleri de tanımlayabilirsiniz. Komut satırı parametreleri ve MSBuild hakkında daha fazla bilgi için bkz. [msbuild Command-Line başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="msbuild-parameters"></a>MSBuild parametreleri
Bir paket oluşturmanın en kolay yolu, MSBuild 'i seçeneğiyle çalıştırmanız `/t:Publish` . Varsayılan olarak, bu komut, projenin kök klasörüyle ilişkili olarak, gibi bir dizin oluşturur `<ProjectDirectory>\bin\Configuration\app.publish\` . Bir Azure projesi oluşturduğunuzda iki dosya oluşturulur: paket dosyasının kendisi ve eşlik eden yapılandırma dosyası:

* Paket dosyası ( `project.cspkg` )
* Yapılandırma dosyası ( `ServiceConfiguration.TargetProfile.cscfg` )

Varsayılan olarak, her bir Azure projesi yerel (hata ayıklama) derlemeler için bir hizmet yapılandırma dosyası ve bulut (hazırlama veya üretim) derlemeleri için bir diğeri içerir. Bununla birlikte, gerektiğinde hizmet yapılandırma dosyalarını ekleyebilir veya kaldırabilirsiniz. Visual Studio içinde bir paket oluşturduğunuzda, paketin yanı sıra hangi hizmet yapılandırma dosyasının dahil edileceğini de sorulacaktır. MSBuild kullanarak bir paket oluşturduğunuzda, yerel hizmet-yapılandırma dosyası varsayılan olarak dahil edilir. Farklı bir hizmet yapılandırma dosyası eklemek için, `TargetProfile` MSBuild komutunun () özelliğini ayarlayın `MSBuild /t:Publish /p:TargetProfile=ProfileName` .

Depolanan paket ve yapılandırma dosyaları için alternatif bir dizin kullanmak istiyorsanız, `/p:PublishDir=Directory\` sonraki ters eğik çizgi ayırıcısı dahil olmak üzere seçeneğini kullanarak yolu ayarlayın.

## <a name="next-steps"></a>Sonraki adımlar
Paket derlendikten sonra Azure 'a dağıtabilirsiniz.
