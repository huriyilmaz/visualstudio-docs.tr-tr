---
title: Projeler ve Çözümler
description: bu belge Mac için Visual Studio içindeki projelere ve çözümlere genel bir bakış sağlar.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 67bb49027e268f272e93fb80de6004a756b8695040450ad4b0d1c2b86912ca29
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121438566"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Mac için Visual Studio projeler ve çözümler

bu makalede, Mac için Visual Studio *proje* ve *çözüm* kavramlarıyla bir genel bakış sunulmaktadır.

> [!NOTE] 
> bu konu Mac için Visual Studio için geçerlidir. Windows Visual Studio için, bkz [Visual Studio projeler ve çözümler](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projeler

Mac için Visual Studio yeni bir uygulama, web sitesi, vb. oluştururken bir proje ile başlar. Proje çalıştırılabilir, kitaplık veya Web sitesini derlemek için gereken tüm dosyaları (kaynak kodu, görüntüler, veri dosyaları vb.) içerir.

Proje, `.csproj` dosya ve klasör hiyerarşisini tanımlayan XML içeren bir dosya (örneğin, C# projeleri için), dosya yolları ve derleme ayarları gibi projeye özel ayarlar tarafından tanımlanır.

Mac için Visual Studio tarafından bir proje yüklendiğinde, çözüm penceresi projenizdeki dosya ve klasörleri göstermek için proje dosyasını kullanır. derleme sırasında, MSBuild çalıştırılabilir dosyayı oluşturmak için proje dosyasındaki ayarları okur.

## <a name="solutions"></a>Çözümler

Bir *çözüm* , bir veya daha fazla ilgili projeyi birlikte gruplandıran bir kapsayıcıdır. Çözümler, kendi benzersiz biçimiyle bir metin dosyası (uzantı) tarafından tanımlanır `.sln` ; el ile düzenlenmesi amaçlanmamıştır.

## <a name="managing-projects-in-the-solution-window"></a>Çözüm penceresinde projeleri yönetme

Proje oluşturulduktan veya yüklendikten sonra proje veya çözümü ve içinde bulunan dosyaları görüntülemek ve yönetmek için çözüm penceresini kullanabilirsiniz. Aşağıdaki çizimde, iki proje içeren bir .NET Core çözümüne sahip çözüm penceresi gösterilmektedir:

![Birden çok projeyle örnek çözüm](media/solution-example.png)

Proje veya çözüm adına çift tıklayarak ya da sağ tıklayıp **Seçenekler**' i seçerek hem projelerin hem de çözümlerin özelliklerini yönetebilirsiniz.

bu seçenekler hakkında daha fazla bilgi, [çözümleri yönetme ve Project özellikleri](managing-solutions-and-project-properties.md) makalesinde sunulmaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio çözümler ve projeler (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
