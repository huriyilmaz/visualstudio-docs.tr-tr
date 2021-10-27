---
title: Windows |'da Docker istemci hatalarını giderme Microsoft Docs
description: Visual Studio kullanarak web uygulamaları oluşturmak ve Docker'a dağıtmak için Windows karşılaştığınız sorunları Visual Studio.
ms.technology: vs-container-tools
author: ghogen
manager: jmartens
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 10/08/2021
ms.author: ghogen
ms.openlocfilehash: 83b4d1cb3053f7e92aec273878337b66399e498a
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350754"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Docker ile Visual Studio geliştirme sorunlarını giderme

Kapsayıcı Araçları'Visual Studio çalışırken, uygulamanızı oluşturmak veya hata ayıklamak için sorunlarla karşılaşabilirsiniz. Aşağıda bazı yaygın sorun giderme adımları verilmiştir.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Daha fazla bilgi için Docker CE'de Windows paylaşımını etkinleştirme (yalnızca Linux kapsayıcıları)

Dosya paylaşımının yalnızca Docker ile Hyper-V kullanıyorsanız yönetiliyor olması gerekir. WSL 2 kullanıyorsanız, aşağıdaki adımlar gerekli değildir ve dosya paylaşımı seçeneği görünmez. Bu sorunu çözmek için:

1. Bildirim alanında **Docker for Windows** sağ tıklayın ve sonra Datele'yi **Ayarlar.**
1. Kaynaklar   >  **Dosya Paylaşımı'ı** seçin ve erişilebilir olması gereken klasörü paylaşın. Sistem sürücünizin tamamını paylaşmak mümkündür ancak önerilmez.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Paylaşılan sürücüler":::

> [!TIP]
> Visual Studio 2017 Visual Studio 15.6'dan sonraki sürümler, **Paylaşılan** Sürücüler yapılandırılmazsa sorur.

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Bunun bir nedeni, kullanıcı profili klasörünüzdeki eski hata ayıklama bileşenlerinin olmasıyla ilgili olabilir. Bu klasörleri kaldırmak için aşağıdaki komutları yürütün; böylece bir sonraki hata ayıklama oturumunda en son hata ayıklama bileşenleri indirilir.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulama hatalarını ayıklarken ağ bağlantısına özgü hatalar

Betiği, konak makinenizin ağ [ile](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)ilgili bileşenlerini yenileyecek Olan Kapsayıcı Ana Bilgisayar Ağına Temizleme'den indirilebilir şekilde yürütmeyi deneyin.

## <a name="mounts-denied"></a>Bağlamalar reddedildi

macOS için Docker kullanırken /usr/local/share/dotnet/sdk/NuGetFallbackFolder klasörüne başvuran bir hatayla karşılaşabilirsiniz. Klasörü Docker'daki Dosya Paylaşımı sekmesine ekleyin.

## <a name="docker-users-group"></a>Docker kullanıcıları grubu

Kapsayıcılarla çalışırken aşağıdaki hatayla Visual Studio hatayla karşılaş alabilirsiniz:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Docker kapsayıcıları ile çalışma izinlerine sahip olmak için 'docker-users' grubunun bir üyesisiniz.  Bir sonraki veya sonraki bir Windows 10 kendinizi gruba eklemek için şu adımları izleyin:

1. Dosyadan Başlat menüsü **Yönetim'i açın.**
1. Yerel **Kullanıcılar ve Gruplar'ı genişletin** ve Gruplar'ı **seçin.**
1. **docker-users grubunu bulun,** sağ tıklayın ve Gruba **ekle'yi seçin.**
1. Kullanıcı hesabı veya hesaplarınızı ekleyin.
1. Bu değişikliklerin etkili olmak için oturum açma ve yeniden oturum açma.

Belirli gruplara kullanıcı `net localgroup` eklemek için Yönetici komut isteminde komutunu da kullanabilirsiniz.

```cmd
net localgroup docker-users DOMAIN\username /add
```

PowerShell'de [Add-LocalGroupMember işlevini](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) kullanın.

## <a name="low-disk-space"></a>Düşük disk alanı

Docker varsayılan olarak görüntüleri genellikle sistem sürücüsünde bulunan *%ProgramData%/Docker/* klasöründe depolar: *C:\ProgramData\Docker \* . Görüntülerin sistem sürücüsü üzerinde değerli alan oluşturmasını önlemek için görüntü klasörü konumunu değiştirebilirsiniz. Bunun için:

 1. Görev çubuğunda Docker simgesine sağ tıklayın ve **Ayarlar.**
 1. **Docker Altyapısı'ı seçin.** 
 1. Düzenleme bölmesinde, `graph` Docker görüntüleri için istediğiniz konumun değeriyle özellik ayarını ekleyin:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Docker daemon ayarlarının ekran görüntüsü":::

Yeniden **Başlat'& Uygula'ya tıklayın.** Bu adımlar *%ProgramData%\docker\config\daemon.json konumundaki yapılandırma dosyasını değiştirir.* Önceden yerleşik görüntüler taşınmaz.

## <a name="container-type-mismatch"></a>Kapsayıcı türü eşleşmez

Bir projeye Docker desteği eklerken bir Windows Linux kapsayıcısı seçersiniz. Docker Server ana bilgisayarı, proje hedefiyle aynı kapsayıcı türünü çalıştıracak şekilde yapılandırılmamışsa büyük olasılıkla aşağıdakine benzer bir hata görebilirsiniz:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Docker Ana Bilgisayarı ve Project Eşleşmesi Ekran Görüntüsü":::

Bu sorunu çözmek için:

- Sistem Tepsisi'nin Windows için Docker simgesine sağ tıklayın ve Kapsayıcılara **Windows...** veya Linux kapsayıcılara **geç... seçeneğini seçin.**

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub

Karşılaştığınız diğer sorunlar için bkz.  [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
