---
title: Windows |'da Docker istemci hatalarını giderme Microsoft Docs
description: Visual Studio kullanarak Windows üzerinde Docker'a web uygulamaları oluşturmak ve dağıtmak için Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235917"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Kapsayıcı Araçları'Visual Studio çalışırken, uygulamanızı oluşturmak veya hata ayıklamak için sorunlarla karşılaşabilirsiniz. Aşağıda bazı yaygın sorun giderme adımları verilmiştir.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Docker CE for Windows ayarlarından birim paylaşımını etkinleştirme (yalnızca Linux kapsayıcıları)

Dosya paylaşımının yalnızca Docker ile Hyper-V kullanıyorsanız yönetiliyor olması gerekir. WSL 2 kullanıyorsanız, aşağıdaki adımlar gerekli değildir ve dosya paylaşımı seçeneği görünmez. Bu sorunu çözmek için:

1. Bildirim alanında **Docker for Windows** sağ tıklayın ve ayarlar'ı **seçin.**
1. Kaynaklar   >  **Dosya Paylaşımı'ı** seçin ve erişilebilir olması gereken klasörü paylaşın. Sistem sürücünizin tamamını paylaşmak mümkündür ancak önerilmez.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Paylaşılan sürücüler":::

> [!TIP]
> Visual Studio 2017 Visual Studio 15.6'dan sonraki sürümler, **Paylaşılan** Sürücüler yapılandırılmamış olduğunda sorulacak.

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Bunun bir nedeni, kullanıcı profili klasörünüzdeki eski hata ayıklama bileşenlerinin olmasıyla ilgili olabilir. Bu klasörleri kaldırmak için aşağıdaki komutları yürütün; böylece bir sonraki hata ayıklama oturumunda en son hata ayıklama bileşenleri indirilir.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulama hatalarını ayıklarken ağ bağlantısına özgü hatalar

Betiği Cleanup [Container Host Networking'tan](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)indirmeyi deneyin. Bu komut dosyası konak makinenizin ağ ile ilgili bileşenlerini yeniler.

## <a name="mounts-denied"></a>Bağlamalar reddedildi

MacOS için Docker kullanırken,/usr/local/share/DotNet/SDK/nugetfallbackfolder klasörüne başvurarak bir hatayla karşılaşabilirsiniz. Klasörü Docker 'daki dosya paylaşma sekmesine ekleyin.

## <a name="docker-users-group"></a>Docker kullanıcıları grubu

Kapsayıcılarla çalışırken Visual Studio 'da aşağıdaki hatayla karşılaşabilirsiniz:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker kapsayıcılarıyla çalışma izinlerinin olması için ' Docker-Users ' grubunun bir üyesi olmanız gerekir.  Windows 10 ' da gruba eklemek için aşağıdaki adımları izleyin:

1. Başlat menüsünden **Bilgisayar Yönetimi**' ni açın.
1. **Yerel kullanıcılar ve gruplar**' ı genişletin ve **gruplar**' ı seçin.
1. **Docker-Users** grubunu bulun, sağ tıklayın ve **gruba ekle**' yi seçin.
1. Kullanıcı hesabınızı veya hesaplarınızı ekleyin.
1. Bu değişikliklerin etkili olması için oturumu kapatın ve yeniden oturum açın.

Ayrıca, `net localgroup` kullanıcıları belirli gruplara eklemek Için yönetici komut isteminde komutunu da kullanabilirsiniz.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell 'de [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) işlevini kullanın.

## <a name="low-disk-space"></a>Yetersiz disk alanı

Docker, varsayılan olarak, görüntüleri genellikle sistem sürücüsünde, * C:\ProgramData\Docker üzerinde bulunan *% ProgramData%/Docker/* klasöründe depolar \* . Görüntülerin sistem sürücüsünde değerli alan almasını engellemek için, görüntü klasörü konumunu değiştirebilirsiniz. Bunun için:

 1. Görev çubuğundaki Docker simgesine sağ tıklayın ve **Ayarlar**' ı seçin.
 1. **Docker altyapısını** seçin. 
 1. Düzen bölmesinde, `graph` Docker görüntüleri için istediğiniz konumun değeri ile özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Docker dosya paylaşımının ekran görüntüsü":::

Yeniden **Başlat'& Uygula'ya tıklayın.** Bu adımlar % *ProgramData%\docker\config\daemon.jsüzerinde* yapılandırma dosyasını değiştirir. Önceden yerleşik görüntüler taşınmaz.

## <a name="container-type-mismatch"></a>Kapsayıcı türü eşleşmez

Projeye Docker desteği eklerken Bir Windows veya Linux kapsayıcısı seçersiniz. Docker Server ana bilgisayarı, proje hedefiyle aynı kapsayıcı türünü çalıştıracak şekilde yapılandırılmamışsa büyük olasılıkla aşağıdakine benzer bir hata görebilirsiniz:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Docker Ana Bilgisayarı ve Proje Eşleşmesi Ekran Görüntüsü":::

Bu sorunu çözmek için:

- Sistem Tepsisi'Docker for Windows simgesine sağ tıklayın ve Windows kapsayıcılara **geç...** veya Linux kapsayıcılara **geçiş... öğesini seçin.**

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub depo

Karşılaştığınız diğer sorunlar için bkz.  [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
