---
title: Kaynak bağlantısı ile NuGet paketlerinde hata ayıklama
description: Bu makalede Mac için Visual Studio içindeki kaynak bağlantısı özelliği açıklanır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451491"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Kaynak bağlantısı ile NuGet paketlerinde hata ayıklama

Kaynak bağlantısı teknolojisi, gönderilen NuGet 'den .NET derlemelerinin kaynak kodu hata ayıklamasını sağlar. Kaynak dosyaların bağlantılarıyla pdb 'leri. Geliştiriciler, NuGet paketini oluştururken ve kaynak denetimi meta verilerini derlemeler ve paket içine katıştırdığınızda kaynak bağlantısı yürütülür. Mac için Visual Studio ' de kaynak bağlantısı etkinleştirildiğinde IDE, yüklü paketler için kaynak dosyalarının kullanılabilir olup olmadığını algılar. Mac için Visual Studio, paket kodunda adım adım ilerlemenize imkan tanıyan bunları indirmek için teklif eder. Kaynak bağlantısı, Xamarin projeleri için mono temel sınıf kitaplığı kodu ile de birlikte çalışarak .NET Framework kodu de adım adım görmenize olanak tanır. Kaynak bağlantısı, harika bir hata ayıklama deneyimi oluşturmak için kaynak denetimi meta verileri sağlar.

> [!NOTE]
> Mac için Visual Studio şu anda sembol sunucularını desteklememektedir. Bu nedenle, sembol sunucularında barındırılan meta verilerle kaynak bağlantı desteklenmez.

## <a name="enable-source-link"></a>Kaynak bağlantısını etkinleştir

Mac için Visual Studio ' de kaynak bağlantısını etkinleştirmek için **Visual Studio > Preferences... > proje hata ayıklayıcısını >** gidin ve **dış kod** onay kutusunun işaretli olduğundan emin olun.

![Dış koda adım gösteren Tercihler iletişim kutusunun ekran görüntüsü](media/source-link1.png)

**Dış kod indirme** bölümündeki ayarı tercihlerinize uyacak şekilde değiştirebilirsiniz:
* Sorun: Mac için Visual Studio dış kodu indirmek isteyip istemediğinizi sorar
* Always: Mac için Visual Studio dış kodu otomatik olarak indirecek
* Hiçbir şekilde: Mac için Visual Studio ilgili harici kodu indirmez

Varsayılan olarak, **ask** seçilidir. Bir NuGet paketi için dış kod bulunduğunda aşağıdaki istemi alırsınız:

![NuGet paketi için dış kod bulunduğunda görüntülenen istem ekran görüntüsü](media/source-link2.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak bağlantısı GitHub deposu](https://github.com/dotnet/sourcelink/blob/master/README.md)
- Kaynak bağlantısı ve paketlere kaynak bağlantısı desteği ekleme hakkında daha fazla bilgi için bkz. [.net belgeleri](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink)
