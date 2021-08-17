---
title: Docker kapsayıcısı üzerinde çalışan bir işleme ekleme
description: Visual Studio kullanarak Docker kapsayıcısı çalıştıran bir uygulamada hata ayıklamayı Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 6a9da6d63bc3ca1d286ae3a3fd785e667fe8f072
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052466"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Docker kapsayıcısı üzerinde çalışan bir işleme ekleme 

Windows Docker Kapsayıcısı'Windows Linux .NET Core Docker kapsayıcısı içinde çalışan uygulamaların hata ayıklamasını Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Linux Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

Visual Studio hata ayıklayıcısını yerel veya uzak makinenizin Linux .NET Core Docker kapsayıcısı içinde çalışan bir işleme eklemek için İşleme Ekle **iletişim** kutusunu kullanabilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için .NET Core Platformlar Arası Geliştirme iş yükünü yüklemeniz ve kaynak koda yerel erişiminizin olması gerekir.

**Linux Docker kapsayıcısı içinde çalışan bir işleme eklemek için:**

1. Bu Visual Studio İşleme Ekle **(CTRL+ALT+P)** > Hata Ayıkla'ya seçerek İşleme Ekle **iletişim** kutusunu açın.

![Docker (Linux Kapsayıcısı) bağlantı türünü gösteren Visual Studio İşleme Ekle iletişim kutusunun ekran görüntüsü.](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Bağlantı türü **olarak** **Docker (Linux Kapsayıcısı) olarak ayarlayın.**
3. Bul... **öğesini** seçerek Docker **Kapsayıcısı** Seç **iletişim kutusu aracılığıyla Bağlantı hedefini** ayarlayın.

    Docker kapsayıcısı işleminin hatasını yerel olarak veya uzaktan ayıkabilirsiniz.

    **Docker kapsayıcısı işleminin hatasını yerel olarak ayıklamak için:**
    1. **Docker CLI ana bilgisayar'ı** Yerel **Makine olarak ayarlayın.**
    1. Listeden eklemek istediğiniz çalışan bir kapsayıcı seçin ve Tamam'a **tıklayın.**

    ![Docker Kapsayıcı Menüsü'ne tıklayın](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Docker kapsayıcı işleminin hatasını uzaktan ayıklamak için:**

    > [!NOTE]
    > Docker kapsayıcısı içinde çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH kullanmak için ilk seçenek, yerel makinenize Docker araçları yüklü değilseniz idealdir.  Yerel olarak docker araçları yüklüyse ve uzak istekleri kabul etmek üzere yapılandırılmış bir Docker daemon'uz varsa, Docker daemon'larını kullanarak ikinci seçeneği deneyin.

    1. ***SSH aracılığıyla uzak bir makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** öğesini seçin.<br/>
        ![Bağlan Sisteme Yükleme](../debugger/media/connect-remote-system.png "Bağlan Sisteme Yükleme")
        1. SSH veya daemon'a başarıyla bağlanın ve Tamam'a bağlanın. 

    1. ***Hedefi [Docker daemon'ı](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla işlem çalıştıran uzak kapsayıcıya ayarlamak için***
        1. Docker ana bilgisayarı (İsteğe **bağlı)** altında daemon adresini (TCP, IP vb.) belirtin ve yenileme bağlantısına tıklayın.
        1. Daemon'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve Tamam'a **tıklayın.**

4. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini  **seçin ve** Ekle'yi seçerek C# kapsayıcı işleminizin hata ayıklamasını Visual Studio!

    ![Visual Studio'daki İşleme Ekle iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Linux Kapsayıcısı) olarak ayarlanır ve dotnet işlemi seçilir.](../debugger/media/docker-attach-complete.png "Tamamlandı Linux Docker Ekleme Menüsü")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Windows Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

İşleme Ekle iletişim kutusunu Visual Studio yerel makinenizin Windows Docker kapsayıcısı içinde çalışan bir işleme hata **ayıklayıcısını** iliştirebilirsiniz.

> [!IMPORTANT]
> Bu özelliği bir .NET Core işlemiyle kullanmak için .NET Core Platformlar Arası Geliştirme iş yükünü yüklemeniz ve kaynak koda yerel erişiminizin olması gerekir.

**Docker kapsayıcısı içinde çalışan bir işleme Windows için:**

1. bu Visual Studio, İşleme **>** Ekle (veya **CTRL+ALT+P**) öğesini seçerek İşleme Ekle **iletişim** kutusunu açın.

   ![Docker Bağlantı türünü (Visual Studio Kapsayıcı) gösteren İşleme Ekle iletişim Windows kutusunun ekran görüntüsü.](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Bağlantı **türü'lerini** **Docker (Windows Container) olarak ayarlayın.**
3. Docker Kapsayıcısı Seç iletişim **kutusunu kullanarak** Bağlantı **hedefini ayarlamak için** **Bul...** öğesini seçin.

    > [!IMPORTANT]
    > Hedef işlem, üzerinde çalıştır konusu olan Docker Windows işlemci mimarisine sahip olması gerekir.

   Hedefi SSH aracılığıyla uzak kapsayıcıya ayarlama şu anda kullanılamıyor ve yalnızca Docker daemon'ı kullanılarak yapılabilir.

    ***Hedefi [Docker daemon'ı](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla işlem çalıştıran uzak kapsayıcıya ayarlamak için***
    1. Docker ana bilgisayarı (İsteğe **bağlı)** altında daemon adresini (TCP, IP vb.) belirtin ve yenileme bağlantısına tıklayın.

    1. Daemon'a başarıyla bağlandıktan sonra iliştirmek için çalışan bir kapsayıcı seçin ve Tamam'ı seçin.

4. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini **seçin ve C#** kapsayıcı **işleminizin** hata ayıklamasını başlatmak için Ekle'yi seçin.

    ![Visual Studio'daki İşleme Ekle iletişim kutusunun ekran görüntüsü. Bağlantı türü Docker (Windows Container) olarak ayarlanır ve dotnet.exe işlemi seçilir.](../debugger/media/docker-attach-complete-windows.png "Docker Windows Menüsü Tamamlandı")

5. Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini  seçin ve C# kapsayıcı işleminizin hata ayıklamasını başlatmak için Ekle'yi seçin.