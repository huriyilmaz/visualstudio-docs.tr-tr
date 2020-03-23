---
title: Source Link ile NuGet paketlerine hata ayıklama
description: Bu makalede, Mac için Visual Studio'daki Kaynak Bağlantı özelliği açıklanmaktadır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451491"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Source Link ile NuGet paketlerine hata ayıklama

Source Link teknolojisi, NuGet o gemiden .NET derlemelerinin kaynak kodunun hata ayıklanmasını sağlar. Kaynak dosyalara bağlantılar içeren PDB'ler. Kaynak Bağlantı, geliştiriciler NuGet paketlerini oluşturduklarında ve kaynak denetimi meta verilerini derlemelerin ve paketin içine yerleştirdiğinde yürütür. Mac için Visual Studio'da Kaynak Bağlantı etkinleştirildiğinde, IDE yüklü paketler için kaynak dosyaların kullanılabilir olup olmadığını algılar. Mac için Visual Studio daha sonra paket kodu ile adım sağlayacak onları indirmek için sunacak. Kaynak Bağlantı ayrıca Xamarin projeleri için Mono Base Sınıf Kitaplığı koduyla çalışır ve .NET Framework koduna adım atmanızı sağlar. Kaynak Bağlantı büyük bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

> [!NOTE]
> Mac için Visual Studio şu anda sembol sunucularını desteklemiyor. Bu nedenle, sembol sunucularında barındırılan meta verilere sahip Kaynak Bağlantı desteklenmez.

## <a name="enable-source-link"></a>Kaynak Bağlantısını Etkinleştir

Mac için Visual Studio'da Kaynak Bağlantısını etkinleştirmek için **Visual Studio > Preferences... > Projeler > Hata Ayıklayıcı'ya** göz atın ve **Dış Koda Adım** onay kutusunun işaretli olduğundan emin olun.

![Dış kod onay kutusuna Adım'ı gösteren tercihler iletişim kutusunun ekran görüntüsü](media/source-link1.png)

**Dış Kodu İndir** ayarını tercihlerinize uyacak şekilde değiştirebilirsiniz:
* Sor: Mac için Visual Studio harici kodu indirmek ister
* Her zaman: Mac için Visual Studio harici kodu otomatik olarak indirecek
* Asla: Mac için Visual Studio ilgili harici kodu indirmez

Varsayılan olarak, **Ask** seçilir. NuGet paketi için harici kod bulunduğunda aşağıdaki komut istemini alırsınız:

![NuGet paketi için harici kod bulunduğunda görünen istem ekran görüntüsü](media/source-link2.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Link GitHub deposu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [.NET belgeleri](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) Kaynak Bağlantı ve paketlere Kaynak Bağlantı desteği nasıl ekleyeceğiniz hakkında daha fazla bilgi için
