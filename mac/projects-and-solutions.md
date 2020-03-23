---
title: Projeler ve Çözümler
description: Bu belge, Mac için Visual Studio'daki Projeler ve Çözümler'e genel bir bakış sağlar.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 92e7a47f7ea2b931c0b923d10e115843d315d024
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70107815"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Projeler ve Çözümler

Bu makalede, Mac için Visual *Studio'da proje* ve *çözüm* kavramlarına genel bir bakış sağlanıyor.

> [!NOTE] 
> Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [Visual Studio'daki Projeler ve çözümlere](/visualstudio/ide/solutions-and-projects-in-visual-studio)bakın.

## <a name="projects"></a>Projeler

Mac için Visual Studio'da yeni bir uygulama, web sitesi vb. oluştururken bir projeyle başlarsınız. Proje, yürütülebilir, kitaplık veya web sitesini derlemek için gereken tüm dosyaları (kaynak kodu, resimler, veri dosyaları, vb.) içerir.

Proje, dosya ve klasör hiyerarşisini tanımlayan `.csproj` xml içeren bir dosya (örneğin, C# projeleri için) tarafından tanımlanır, dosyalara giden yollar ve yapı ayarları gibi projeye özgü ayarlar.

Bir proje Mac için Visual Studio tarafından yüklendiğinde, Solution Pad projenizdeki dosya ve klasörleri görüntülemek için proje dosyasını kullanır. Derleme sırasında MSBuild, yürütülebilir liği oluşturmak için proje dosyasındaki ayarları okur.

## <a name="solutions"></a>Çözümler

*Çözüm,* bir veya daha fazla ilgili projeyi bir araya getiren bir kapsayıcıdır. Çözümler, kendi benzersiz biçimine `.sln`sahip bir metin dosyası (uzantı) tarafından açıklanır; elle düzenlenmesi amaçlanmamıştır.

## <a name="managing-projects-in-the-solution-pad"></a>Çözüm Defteri'nde Projeleri Yönetme

Bir proje oluşturulduktan veya yüklendikten sonra, projeyi veya çözümü ve içerdiği dosyaları görüntülemek ve yönetmek için Çözüm Defteri'ni kullanabilirsiniz. Aşağıdaki resimde, iki proje içeren bir .NET Core çözümlü Çözüm Pedi gösterilmektedir:

![Birden fazla projeile örnek çözüm](media/solution-example.png)

Proje veya çözüm adını çift tıklatarak veya **Seçenekler'i**sağ tıklayıp seçerek hem projelerin hem de çözümlerin özelliklerini yönetebilirsiniz.

Bu seçenekler hakkında daha fazla bilgi [Çözümleri Ve Proje Özelliklerini Yönetme](managing-solutions-and-project-properties.md) makalesinde verilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da çözümler ve projeler (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
