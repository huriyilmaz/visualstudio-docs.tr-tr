---
title: kaynak bağlantısı ile NuGet paketlerine hata ayıklama
description: bu makalede Mac için Visual Studio içindeki kaynak bağlantısı özelliği açıklanır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 307196dc7e33d268c45a9bb126c002ad426c5558
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725975"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>kaynak bağlantısı ile NuGet paketlerine hata ayıklama

kaynak bağlantısı teknolojisi, tarafından gönderilen NuGet .net derlemelerinin kaynak kodu hata ayıklamalarını sağlar. Kaynak dosyaların bağlantılarıyla pdb 'leri. geliştiriciler NuGet paketini oluştururken ve kaynak denetimi meta verilerini derlemeler ve paketler içine eklerken kaynak bağlantısı yürütülür. Mac için Visual Studio ' de kaynak bağlantısı etkinleştirildiğinde ıde, yüklü paketler için kaynak dosyalarının kullanılabilir olup olmadığını algılar. Mac için Visual Studio, paket kodunda adım adım ilerlemenize imkan tanıyan bunları indirmek için teklif eder. kaynak bağlantısı, Xamarin projeleri için Mono temel sınıf kitaplığı kodu ile de birlikte çalışarak .NET Framework kodu de adım adım görmenize olanak tanır. Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

> [!NOTE]
> Mac için Visual Studio şu anda sembol sunucularını desteklememektedir. Bu nedenle, sembol sunucularında barındırılan meta verilerle kaynak bağlantı desteklenmez.

## <a name="enable-source-link"></a>Kaynak bağlantısını etkinleştir

Mac için Visual Studio kaynak bağlantısını etkinleştirmek için, **Visual Studio > tercihleri... > projeler > hata ayıklayıcıya** gidin ve **dış kod** onay kutusunun işaretli olduğundan emin olun.

![Dış koda adım gösteren Tercihler iletişim kutusunun ekran görüntüsü](media/source-link1.png)

**Dış kod indirme** bölümündeki ayarı tercihlerinize uyacak şekilde değiştirebilirsiniz:
* sorun: Mac için Visual Studio dış kodu indirmek isteyip istemediğinizi sorar
* Always: Mac için Visual Studio dış kodu otomatik olarak indirecek
* hiçbir şekilde: Mac için Visual Studio ilgili harici kodu indirmez

Varsayılan olarak, **ask** seçilidir. NuGet paketi için dış kod bulunduğunda aşağıdaki istemi alırsınız:

![NuGet paketi için dış kod bulunduğunda görüntülenen istem ekran görüntüsü](media/source-link2.png)


## <a name="see-also"></a>Ayrıca bkz.

- [kaynak bağlantısı GitHub deposu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- Kaynak bağlantısı ve paketlere kaynak bağlantısı desteği ekleme hakkında daha fazla bilgi için bkz. [.net belgeleri](/dotnet/standard/library-guidance/sourcelink)