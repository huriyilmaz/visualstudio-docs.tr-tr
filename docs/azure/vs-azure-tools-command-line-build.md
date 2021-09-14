---
title: Azure için komut satırı derlemesi | Microsoft Docs
description: Azure için komut satırı derlemesi
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: eec0fdc1ddfbeee3ae7a23502186d7ee35d5b979
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633209"
---
# <a name="building-azure-projects-from-the-command-line"></a>Komut satırından Azure projeleri oluşturma
Microsoft Build Engine (MSBuild) kullanarak, derleme laboratuvarı ortamlarında Visual Studio yüklü olmayan ürünler oluşturabilirsiniz. MSBuild, Microsoft tarafından genişletilebilir ve tam olarak desteklenen proje dosyaları için bir XML biçimi kullanır. MSBuild dosya biçimini kullanarak bir veya daha fazla platform ve yapılandırma için hangi öğelerin oluşturulması gerektiğini tanımlayabilirsiniz.

ayrıca, komut satırında MSBuild de çalıştırabilirsiniz ve bu konuda bu yaklaşım açıklanır. Komut satırındaki özellikleri ayarlayarak, bir proje için özel konfigürasyonlar oluşturabilirsiniz. Benzer şekilde, MSBuild derlemelerin hedeflerini de tanımlayabilirsiniz. komut satırı parametreleri ve MSBuild hakkında daha fazla bilgi için bkz. [MSBuild Command-Line başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="msbuild-parameters"></a>MSBuild parametreleri
bir paket oluşturmanın en kolay yolu, ' i seçeneğiyle MSBuild çalıştırmalıdır `/t:Publish` . Varsayılan olarak, bu komut, projenin kök klasörüyle ilişkili olarak, gibi bir dizin oluşturur `<ProjectDirectory>\bin\Configuration\app.publish\` . Bir Azure projesi oluşturduğunuzda iki dosya oluşturulur: paket dosyasının kendisi ve eşlik eden yapılandırma dosyası:

* Paket dosyası ( `project.cspkg` )
* Yapılandırma dosyası ( `ServiceConfiguration.TargetProfile.cscfg` )

Varsayılan olarak, her bir Azure projesi yerel (hata ayıklama) derlemeler için bir hizmet yapılandırma dosyası ve bulut (hazırlama veya üretim) derlemeleri için bir diğeri içerir. Bununla birlikte, gerektiğinde hizmet yapılandırma dosyalarını ekleyebilir veya kaldırabilirsiniz. Visual Studio içinde bir paket oluşturduğunuzda, paketin yanı sıra hangi hizmet yapılandırma dosyasının dahil edileceğini sorulur. MSBuild kullanarak bir paket oluşturduğunuzda, yerel hizmet-yapılandırma dosyası varsayılan olarak dahil edilir. farklı bir hizmet yapılandırma dosyası eklemek için, `TargetProfile` MSBuild komutunun () özelliğini ayarlayın `MSBuild /t:Publish /p:TargetProfile=ProfileName` .

Depolanan paket ve yapılandırma dosyaları için alternatif bir dizin kullanmak istiyorsanız, `/p:PublishDir=Directory\` sonraki ters eğik çizgi ayırıcısı dahil olmak üzere seçeneğini kullanarak yolu ayarlayın.

## <a name="next-steps"></a>Sonraki adımlar
Paket derlendikten sonra Azure 'a dağıtabilirsiniz.
