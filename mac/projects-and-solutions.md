---
title: Projeler ve Çözümler
description: Bu belgede, Mac için Visual Studio'daki Projelere ve Çözümlere genel bir bakış Mac için Visual Studio.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/09/2021
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 33f6c5b6b8a536355da1b9416c3b316996f4b245
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350722"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Projeler ve Çözümler

Bu makalede, Mac için Visual Studio'daki *proje ve çözüm* kavramlarına genel bir bakış Mac için Visual Studio. 

> [!NOTE] 
> Bu konu, Mac için Visual Studio. Visual Studio hakkında daha fazla Windows için [bkz.](/visualstudio/ide/solutions-and-projects-in-visual-studio)Visual Studio.

## <a name="projects"></a>Projeler

Yeni bir uygulama, web sitesi vb. oluştururken Mac için Visual Studio bir projeyle başlarız. Proje yürütülebilir dosyayı, kitaplığı veya web sitesini derlemek için gereken tüm dosyaları (kaynak kodu, görüntüler, veri dosyaları vb.) içerir.

Proje, dosya ve klasör hiyerarşisini tanımlayan xml dosyasını, dosyaların yollarını ve derleme ayarları gibi projeye özgü ayarları içeren bir dosya `.csproj` (örneğin, C# projeleri için) tarafından tanımlanır.

Proje, proje tarafından Mac için Visual Studio, Çözüm Penceresi projenizin dosya ve klasörlerini görüntülemek için proje dosyasını kullanır. Derleme sırasında MSBuild proje dosyasından yürütülebilir dosyayı oluşturmak için ayarları okur.

## <a name="solutions"></a>Çözümler

*Çözüm,* bir veya daha fazla ilgili projeyi grup halinde gruplatan bir kapsayıcıdır. Çözümler, kendi benzersiz biçimine sahip bir metin dosyası (uzantı) tarafından açıklanmıştır; el `.sln` ile düzenlenemez.

## <a name="managing-projects-in-the-solution-window"></a>Çözüm Penceresinde Projeleri Yönetme

Proje oluşturulduktan veya yüklendiktan sonra, projeyi veya çözümü ve içinde yer alan dosyaları görüntülemek ve yönetmek için Çözüm Penceresi'nin kullanabilirsiniz. Aşağıdaki çizimde, iki proje içeren bir .NET Core çözümüne sahip Çözüm Penceresi gösterilir:

![Birden çok proje içeren örnek çözüm](media/solution-example.png)

Proje veya çözüm adına çift tıklayarak veya sağ tıklar ve Seçenekler'i seçerek hem projelerin hem de çözümlerin özelliklerini **yönetebilirsiniz.**

Bu seçenekler hakkında daha fazla bilgi, Çözümleri [Yönetme ve Özellikleri Project sağlanır.](managing-solutions-and-project-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'de çözümler ve projeler (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
