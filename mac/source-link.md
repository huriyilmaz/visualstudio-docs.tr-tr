---
title: Kaynak Bağlantısı ile NuGet paketlerinde hata ayıklama
description: Bu makalede, Mac için Visual Studio'daki Kaynak Bağlantısı özelliği açıklanmıştır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964818"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Kaynak Bağlantısı ile NuGet paketlerinde hata ayıklama

Kaynak Bağlantı teknolojisi, ile birlikte gelen .NET derlemelerinin kaynak kodunda NuGet hata ayıklamasını sağlar. Kaynak dosyaların bağlantılarını içeren PDB'ler. Kaynak Bağlantısı, geliştiriciler kendi derleme paketini NuGet derlemelere ve pakete kaynak denetimi meta verilerini katıştırarak yürütür. Kaynak Bağlantı bu Mac için Visual Studio etkinleştirildiğinde, IDE kaynak dosyalarının yüklü paketler için kullanılabilir olup olduğunu algılar. Mac için Visual Studio, bunları indirmeyi teklif ediyor ve paket kodunda adım adım size yol sunuyor. Kaynak Bağlantı ayrıca Xamarin projeleri için Mono Temel Sınıf Kitaplığı koduyla birlikte çalışır ve bu koda .NET Framework olanak sağlar. Kaynak Bağlantı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

> [!NOTE]
> Mac için Visual Studio şu anda sembol sunucularını desteklemez. Bu nedenle, sembol sunucularında barındırılan meta verilere sahip Kaynak Bağlantı desteklenmiyor.

## <a name="enable-source-link"></a>Kaynak Bağlantısını Etkinleştirme

Mac için Visual Studio'da Kaynak Bağlantısını etkinleştirmek için **Visual Studio > Tercihler... > Proje** > Hata Ayıklayıcısı'nın  ardından Dış koda adımla onay kutusunun işaretli olduğundan emin olun.

![Dış koda adımla onay kutusunu gösteren tercihler iletişim kutusunun ekran görüntüsü](media/source-link1.png)

Dış Kodu İndir'de **ayarını tercihlerinize** uyacak şekilde değiştirebilirsiniz:
* Sorun: Mac için Visual Studio kodu indirmeniz istenecek
* Her zaman: Mac için Visual Studio dış kodu otomatik olarak indirir
* Hiçbir Mac için Visual Studio ilgili dış kodu indirmeyebilirsiniz

Varsayılan olarak **Sor** seçilidir. Bir paket için dış kod bulunurken aşağıdaki NuGet alırsınız:

![Bir paket için dış kod bulunduğu zaman görüntülenen istemin ekran NuGet görüntüsü](media/source-link2.png)


## <a name="see-also"></a>Ayrıca bkz.

- Kaynak [Bağlantı GitHub deposu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Kaynak Bağlantısı ile](/dotnet/standard/library-guidance/sourcelink) ilgili .NET belgeleri ve paketlere Kaynak Bağlantı desteği ekleme hakkında daha fazla bilgi için