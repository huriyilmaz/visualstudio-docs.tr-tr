---
title: Kaynak Bağlantısı ile NuGet paketlerinde hata ayıklama
description: Bu makalede, Mac için Visual Studio'daki Kaynak Bağlantısı özelliği açıklanmıştır.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 12/16/2019
ms.topic: conceptual
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: a5cecf4d3065a889e9ab48b9fc94e91341f778e7
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804617"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Kaynak Bağlantısı ile NuGet paketlerinde hata ayıklama

Kaynak Bağlantı teknolojisi, ile birlikte gelen .NET derlemelerinin kaynak kodunda hata NuGet hata ayıklamasını sağlar. Kaynak dosyaların bağlantılarını içeren PDB'ler. Kaynak Bağlantısı, geliştiriciler kendi derleme paketini NuGet derlemelere ve pakete kaynak denetimi meta verilerini katıştırarak yürütür. Kaynak Bağlantı bu Mac için Visual Studio etkinleştirildiğinde, IDE kaynak dosyalarının yüklü paketler için kullanılabilir olup olduğunu algılar. Mac için Visual Studio paket kodunda adım size yol sağlayacak şekilde indirme teklifi sunar. Kaynak Bağlantı ayrıca Xamarin projeleri için Mono Temel Sınıf Kitaplığı koduyla birlikte çalışır ve bu koda .NET Framework olanak sağlar. Kaynak Bağlantı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

> [!NOTE]
> Mac için Visual Studio şu anda sembol sunucularını desteklemez. Bu nedenle, sembol sunucularında barındırılan meta verilere sahip Kaynak Bağlantı desteklenmiyor.

## <a name="enable-source-link"></a>Kaynak Bağlantısını Etkinleştir

Mac için Visual Studio'da Kaynak Bağlantısını etkinleştirmek için **Visual Studio > Tercihler... >** Proje > Hata Ayıklayıcısı'nın  ardından Dış koda adımla onay kutusunun işaretli olduğundan emin olun.

![Dış koda adımla onay kutusunu gösteren tercihler iletişim kutusunun ekran görüntüsü](media/source-link1.png)

Dış Kodu İndir'de **ayarı tercihlerinize** uyacak şekilde değiştirebilirsiniz:
* Sorun: Mac için Visual Studio kodu indirmeniz istenecek
* Her zaman: Mac için Visual Studio dış kodu otomatik olarak indirir
* Hiçbir zaman Mac için Visual Studio ilgili dış kodu indirmeyebilirsiniz

Varsayılan olarak **Sor** seçilidir. Bir paket için dış kod bulunurken aşağıdaki NuGet alırsınız:

![Bir paket için dış kod bulunsa görüntülenen istemin NuGet görüntüsü](media/source-link2.png)


## <a name="see-also"></a>Ayrıca bkz.

- Kaynak [Bağlantı GitHub deposu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Kaynak Bağlantısı ile](/dotnet/standard/library-guidance/sourcelink) ilgili .NET belgeleri ve paketlere Kaynak Bağlantı desteği ekleme hakkında daha fazla bilgi için