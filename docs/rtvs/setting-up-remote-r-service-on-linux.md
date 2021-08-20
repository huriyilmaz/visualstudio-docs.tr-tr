---
title: Linux'ta Uzak R Hizmeti Ayarlama
description: Ubuntu ve Linux için Windows Alt Sistemi'da Uzak R Hizmeti'Linux için Windows Alt Sistemi.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: badd4cda94055a4c3d50a1a82a1dce6e52a3365c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060498"
---
# <a name="remote-r-service-for-linux"></a>Linux için Uzak R Hizmeti

Linux için Uzak R Hizmeti şu anda rtvs-daemon olarak paketlenmiştir. Daemon Ubuntu 16.04, 16.10 LTS masaüstü, sunucu ve Ubuntu çalıştıran Linux için Windows Alt Sistemi test edilir. Bu makalenin büyük bölümü, bu farklı sistemlerde Uzak R Hizmeti ayarlamaya ilişkin yönergeler sağlar.

Uzak makineyi yapılandırdıktan sonra, aşağıdaki adımlar Visual Studio için R Araçları (RTVS) hizmetini bu hizmete bağlamış olur:

1. R   >    >  **Araçları'Windows'ı seçerek** Çalışma **Alanları penceresini** açın.
1. Bağlantı **Ekle'yi seçin.**
1. Bağlantı için bir ad girin ve URL'sini `https://localhost:5444` (Linux için Windows Alt Sistemi) `https://public-ip:5444` veya (Azure kapsayıcısı) belirtin. Tamamlandığında **Kaydet'i** seçin.
1. Bağlantı simgesini seçin veya bağlantı öğesini çift tıklatın.
1. Oturum açma kimlik bilgilerini girin. Kullanıcı adı , içinde olduğu gibi ön `<<unix>>\` eke sahip olmalıdır (Linux uzak `<<unix>>\ruser1` bilgisayarlarına tüm bağlantılar için gerektiği gibi).
1. Otomatik olarak imzalanan sertifika kullanıyorsanız bir uyarıyla karşınız olabilir. İleti, uyarıyı düzeltmeye ilişkin yönergeler sağlar.

## <a name="set-up-remote-r-service"></a>Uzak R Hizmeti Ayarlama

Bu bölüm aşağıdaki seçenekleri açıklar:

- [Fiziksel Ubuntu bilgisayarı](#physical-ubuntu-computer)
- [Azure'da Ubuntu Server VM Veri Bilimi VM'si sanal makinesi](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Yerel veya uzak Docker kapsayıcısı (temiz derleme)](#local-or-remote-docker-container-clean-build)
- [Kapsayıcı üzerinde Azure Container Instances](#container-running-on-azure-container-instances)

Her durumda, uzak bilgisayarda aşağıdaki R yorumlayıcılarından biri yüklü olmalıdır:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [Windows için CRAN R](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fiziksel Ubuntu bilgisayarı

1. Bilgisayarda oturum açtıktan sonra rtvs-daemon tarball'u indirin:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Yükleme betiği çalıştırın:

    ```bash
    sudo ./rtvs-install
    ```

    Sessiz otomasyon için `sudo ./rtvs-install -s` kullanın.

1. Hizmeti etkinleştirme ve başlatma:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. SSL sertifikasını yapılandırın (üretim için gereklidir). Varsayılan olarak, rtvs-daemon paket `ssl-cert-snakeoil.pem` tarafından `ssl-cert-snakeoil.pem` oluşturulan ve `ssl-cert` kullanır. Yükleme sırasında , içinde `ssl-cert-snakeoil.pfx` birleştirilmiştir. Üretim amacıyla, yöneticiniz tarafından sağlanan SSL sertifikasını kullanın. SSL sertifikası, üzerinde bir *.pfx* dosyası ve isteğe bağlı içeri aktarma parolası sağlayarak *yalıtabilirsiniz: /etc/rtvs/rtvsd.config.js.*

1. (İsteğe bağlı) Hizmetin çalıştırılıp çalışmay olduğunu kontrol edin:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Kullanıcı adı altında çalışan bir işlem `rtvssvc` görmüyorsanız. Aşağıdaki komutu kullanarak başlatabilirsiniz:

    ```bash
    sudo systemctl start rtvsd
    ```

1. rtvs-daemon'ı daha fazla yapılandırmak için bkz. `man rtvsd` .

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Azure'da Ubuntu Server VM Veri Bilimi VM'si sanal makinesi

#### <a name="create-a-vm"></a>VM oluşturma

1. [Azure Portal](https://portal.azure.com)’ında oturum açın.
1. Sanal Makineler'e gidin ve Ekle'yi **seçin.**
1. Kullanılabilir VM görüntüleri listesinde, arama yapın ve aşağıdakilerden birini seçin:
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - Veri Bilimi VM'si: `Linux Data Science` (ayrıntılar [için bkz. Veri Bilimi](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) Sanal Makineleri)
1. Dağıtım modelini olarak ayarlayın ve `Resource manager` **Oluştur'a seçin.**
1. VM için bir ad seçin, kullanıcı adı ve parola girin (parola gereklidir çünkü SSH ortak anahtarıyla oturum açma desteklenmiyor).
1. VM yapılandırmasında istenen diğer değişiklikleri yapın.
1. Bir VM boyutu seçin, yapılandırmayı doğrulayın ve **Oluştur'a seçin.** VM oluşturulduktan sonra sonraki bölüme ilerleyin.

#### <a name="configure-the-vm"></a>VM'yi yapılandırma

1. VM'nin Ağ **İletişimi bölümünde,** izin verilen gelen bağlantı noktası olarak 5444'ü ekleyin. Farklı bir bağlantı noktası kullanmak için RTVS daemon yapılandırma dosyasındaki (*/etc/rtvs/rtvsd.config.jsayarını ).*
1. (İsteğe bağlı) BIR DNS adı ayarlayın; IP adresini de kullanabilirsiniz.
1. Bağlan için PuTTY gibi bir SSH istemcisi kullanarak VM'ye Windows.
1. Yukarıdaki Fiziksel [Ubuntu bilgisayarı yönergelerini](#physical-ubuntu-computer) izleyin.

### <a name="windows-subsystem-for-linux-wsl"></a>Linux için Windows Alt Sistemi (WSL)

1. [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) veya Windows Server için WSL [yükleme yönergelerini izleyin.](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl)
1. Bash'i Windows ve önceki yönergeleri izleyin ve tek bir özel durum dışında bir Fiziksel [Ubuntu](#physical-ubuntu-computer) bilgisayarı. WSL şu anda systemd/systemctl arabirimlerini desteklemey olduğundan, 3. adım için hizmeti onun `rtvsd` yerine komutunu kullanarak başlatabilirsiniz.

### <a name="local-or-remote-docker-container-clean-build"></a>Yerel veya uzak Docker kapsayıcısı (temiz derleme)

1. Aşağıdaki içeriklere sahip bir Docker dosyası oluşturun. Bu dosya Uzak R hizmeti daemon'unu ve en son R sürümünü yüklüdür. **Not:** Bu betik, son iki deyimde istediğiniz gibi değiştirebilecek "foobar" parolasıyla "ruser1" adlı bir kullanıcı `RUN` oluşturur.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Docker dosyasını derleme ve çalıştırma:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. IÇEREN'e RTVS'den bağlanmak için yol, kullanıcı adı `https://localhost:5444` ve parola olarak `<<unix>>\ruser1` `foobar` kullanın. Kapsayıcı uzak bir bilgisayarda çalışıyorsa yol `https://remote-host-name:5444` olarak kullanın. Bağlantı noktası, üzerinde */etc/rtvs/rtvsd.config.jsdeğiştirilebilir.*

### <a name="container-running-on-azure-container-instances"></a>Kapsayıcı üzerinde Azure Container Instances

1. Görüntüyü oluşturmak için [Yerel veya uzak Docker kapsayıcısı (temiz derleme)](#local-or-remote-docker-container-clean-build) yönergelerini izleyin.
1. Kapsayıcıyı Docker hub'ına veya Azure Container Repository'ye itin.
1. Azure CLI'sini başlatma ve komutunu kullanarak oturum `az login` açma.
1. Kapsayıcıyı hizmet olarak çalıştıracak şekilde ayarlamadıysanız komutunu kullanarak `az container create` `--command-line "rtvsd"` `rtvsd` kapsayıcıyı `systemd` oluşturun. Aşağıdaki komutta görüntünün Docker hub'larında olması beklenir. Komut satırına Container Repository kimlik bilgisi bağımsız değişkenleri ekleyerek de Azure Container Repository'i kullanabilirsiniz.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Durumu `az container list` kontrol etmek için komutunu kullanın. için `provisioningState` bakın: `Succeeded` .
1. Sağlama başarılı olursa artık kapsayıcıya bağlanabilirsiniz. Alanında, RTVS'den kapsayıcıya bağlanmak için docker dosyasındaki kimlik bilgileriyle birlikte kullanabileceğiniz genel IP `ipAddress` adresini bulun.
