---
title: ARM ile desteklenen cihazlarda Visual Studio
description: ARM tabanlı işlemcilerle cihazlarda Visual Studio kullanmak için Öneriler.
ms.date: 09/10/2020
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1e45422b8b1f3dd98ec8c47c4788d935263f7f50
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094875"
---
# <a name="visual-studio-on-arm-powered-devices"></a>ARM destekli cihazlarda Visual Studio

> [!IMPORTANT]
> Visual Studio yalnızca x86 veya AMD64/x64 tabanlı işlemci kullanan cihazlarda desteklenir.

Visual Studio, x86 mimarisine bağlı olarak hedef işlemcilerle oluşturulmuştur ve ARM tabanlı işlemciler için Visual Studio sürümü yoktur. ancak, Windows [ARM üzerinde x86 öykünmesi](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation)sağlar ve bu Visual Studio çalıştırılabilir. x86 öykünmesi aracılığıyla bir ARM işlemcisinde Visual Studio çalıştırmak Visual Studio performansını önemli ölçüde impairs ve Visual Studio çeşitli özellikleri bu senaryoda çalışmak üzere tasarlanmamıştır. bu nedenle, ARM tabanlı işlemciler kullanan cihazlarda Visual Studio çalıştırmayı önermiyoruz ve bunun yerine uzaktan hedeflenen ARM cihazlarını öneririz.

## <a name="remote-targeting-arm-devices"></a>ARM cihazlarını uzaktan hedefleme
en iyi deneyim için, ayrı, x86 ile desteklenen bir bilgisayarda Visual Studio kullanmanızı ve ARM tabanlı cihazı hedeflemek için Visual Studio uzaktan dağıtımı ve hata ayıklama özelliklerini kullanmanızı öneririz. cihazda zaten yüklü olan Windows evrensel uygulamalarda hata ayıklamak için bkz. [yüklü uygulama paketini hata ayıkla](../debugger/debug-installed-app-package.md) belgeleri. yeni bir uygulama dağıtmak için bkz. [Windows mağazası uygulaması uzak tley 'i çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md). Diğer tüm uygulama türleri için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) belgeleri.

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>ARM cihazlarda Visual Studio çalıştırmak için İpuçları

### <a name="use-only-when-needed"></a>Yalnızca gerektiğinde kullanın
yalnızca ARM 'e özgü çalışma için gerektiğinde Visual Studio kullanarak zamandan iyileştirin. ARM ile desteklenen herhangi bir cihazda performans kötü olur ve bu da normal kullanım için kabul edilemez olduğunu fark edersiniz.

### <a name="install-time"></a>Yükleme saati
yüklemeyi daha uzun sürecek Visual Studio planlayın ve zaman aralıklarını duraklatıp veya yeniden başlatma gerekir.
 
### <a name="remote-tools"></a>Uzak araçlar
Uzak cihazda çalışan bir uygulamada hata ayıklamak için, ARM için [Uzak araçları indirip yüklemeniz](../debugger/remote-debugging.md#download-and-install-the-remote-tools) gerekir.

### <a name="start-debugging-f5"></a>Hata ayıklamayı Başlat (F5)
tüm Visual Studio projeleri, bir ARM cihazından hata ayıklamayı başlattığınızda (**F5**) projeleri yerel olarak başlatacak şekilde yapılandırılmamıştır. uygulamanız yerel olarak çalışıyor olsa bile, uzaktan hata ayıklama için Visual Studio yapılandırmanız gerekebilir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Yardımımız olması gerekir!
ARM cihazlarda yerel olarak çalıştırmak Visual Studio isterseniz, gerekli senaryolar ve destek hakkında bilgi almak istiyoruz. [Geliştirici topluluğu](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html)' na giderek bizimle iletişime ulaşabilirsiniz.
