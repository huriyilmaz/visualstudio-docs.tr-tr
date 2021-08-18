---
title: Azure | için komut satırı derlemesi Microsoft Docs
description: Azure için komut satırı derlemesi
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: eec0fdc1ddfbeee3ae7a23502186d7ee35d5b979
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082354"
---
# <a name="building-azure-projects-from-the-command-line"></a>Komut satırdan Azure projeleri bina
Microsoft Build Engine (MSBuild) kullanarak, derleme laboratuvarı ortamlarında Visual Studio derleme ortamları kurabilirsiniz. MSBuild, Microsoft tarafından genişletilebilir ve tam olarak desteklenen proje dosyaları için bir XML biçimi kullanır. Dosya MSBuild kullanarak, bir veya daha fazla platform ve yapılandırma için hangi öğelerin oluşturması gerektiğini açıklayın.

Komut satırına MSBuild da çalıştırabilirsiniz ve bu konuda bu yaklaşım açıklanmıştır. Komut satırı özelliklerini ayarerek bir projenin belirli yapılandırmalarını oluşturabilirsiniz. Benzer şekilde, derlemeleri oluşturmak için MSBuild tanımlayabilirsiniz. Komut satırı parametreleri ve komut satırı parametreleri hakkında daha fazla MSBuild için [bkz. MSBuild Command-Line Başvurusu.](../msbuild/msbuild-command-line-reference.md)

## <a name="msbuild-parameters"></a>MSBuild parametreleri
Paket oluşturmanın en basit yolu, MSBuild `/t:Publish` çalıştırmaktır. Varsayılan olarak, bu komut projenin kök klasörüyle ilişkili olarak gibi bir dizin `<ProjectDirectory>\bin\Configuration\app.publish\` oluşturur. Bir Azure projesi derlemeniz için iki dosya oluşturulur: paket dosyasının kendisi ve eşlik eden yapılandırma dosyası:

* Paket Dosyası ( `project.cspkg` )
* Yapılandırma Dosyası ( `ServiceConfiguration.TargetProfile.cscfg` )

Varsayılan olarak, her Azure projesi yerel (hata ayıklama) derlemeleri için bir hizmet yapılandırma dosyası ve bulut (hazırlama veya üretim) derlemeleri için başka bir hizmet yapılandırma dosyası içerir. Ancak, gerektiğinde hizmet yapılandırma dosyalarını ekleyebilir veya kaldırabilirsiniz. Uygulama içinde bir paket Visual Studio paketin yanı sıra hangi hizmet yapılandırma dosyasının dahil etmek istediğiniz soruldu. MSBuild kullanarak bir paket MSBuild yerel hizmet yapılandırma dosyası varsayılan olarak dahil edilir. Farklı bir hizmet yapılandırma dosyası eklemek için MSBuild `TargetProfile` komutunun () özelliğini `MSBuild /t:Publish /p:TargetProfile=ProfileName` ayarlayın.

Depolanan paket ve yapılandırma dosyaları için alternatif bir dizin kullanmak için, sonda ters eğik çizgi ayırıcısı da dahil olmak üzere seçeneğini kullanarak `/p:PublishDir=Directory\` yolu ayarlayın.

## <a name="next-steps"></a>Sonraki adımlar
Paket hazır olduktan sonra Azure'a dağıtabilirsiniz.
