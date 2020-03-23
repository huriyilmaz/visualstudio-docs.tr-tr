---
title: Uzak Linux bilgisayarlarda Hata Ayıklama Python kodu
description: Gerekli yapılandırma adımları, güvenlik ve sorun giderme gibi uzak Linux bilgisayarlarda çalışan Python kodunu hata ayıklamak için Visual Studio'yı kullanın.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e718a5610d9539e3e2a89af0a9de502ebfd168a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62962567"
---
# <a name="remotely-debug-python-code-on-linux"></a>Linux'ta Python kodunu uzaktan hata ayıklama

Visual Studio, Python uygulamalarını Windows bilgisayarında yerel ve uzaktan başlatabilir ve hata ayıklayabilir (bkz. [Uzaktan hata ayıklama).](../debugger/remote-debugging.md) Ayrıca, [ptvsd kitaplığını](https://pypi.python.org/pypi/ptvsd)kullanarak CPython dışında farklı bir işletim sistemi, aygıt veya Python uygulamasında uzaktan hata ayıklayabilir.

Ptvsd kullanırken, Python kodunun debugged olan Visual Studio takabilirsiniz hata ayıklama sunucusu barındırır. Bu barındırma, sunucuyu almak ve etkinleştirmek için kodunuzda küçük bir değişiklik gerektirir ve uzak bilgisayarda TCP bağlantılarına izin vermek için ağ veya güvenlik duvarı yapılandırmaları gerektirebilir.

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | Uzaktan hata ayıklama nın tanıtımı için, Visual Studio 2015 ve 2017 için geçerli olan [Deep Dive: Cross-platform uzaktan hata ayıklama](https://youtu.be/y1Qq7BrV6Cc) (youtube.com, 6m22s) bölümüne bakın. |

## <a name="set-up-a-linux-computer"></a>Linux bilgisayarı ayarlama

Bu izbu izlemeyi izlemek için aşağıdaki öğeler gereklidir:

- Mac OSX veya Linux gibi bir işletim sistemi üzerinde Python çalıştıran uzak bir bilgisayar.
- Bağlantı noktası 5678 (gelen) uzaktan hata ayıklama için varsayılan olan bilgisayarın güvenlik duvarında açıldı.

[Azure'da](/azure/virtual-machines/linux/creation-choices) kolayca bir Linux sanal makinesi oluşturabilir ve Windows'tan [Uzak Masaüstü'nü kullanarak bu](/azure/virtual-machines/linux/use-remote-desktop) makineye erişebilirsiniz. Python varsayılan olarak yüklü olduğundan VM için Ubuntu uygundur; aksi takdirde, ek Python indirme konumları için [seçtiğiniz bir Python yorumlayıcısı](installing-python-interpreters.md) yükleyin'deki listeye bakın.

Bir Azure VM için güvenlik duvarı kuralı oluşturma yla ilgili ayrıntılar için Azure [portalını kullanarak Azure'da VM bağlantı noktalarıaç'a](/azure/virtual-machines/windows/nsg-quickstart-portal)bakın.

## <a name="prepare-the-script-for-debugging"></a>Komut dosyasını hata ayıklama için hazırlayın

1. Uzak bilgisayarda, aşağıdaki kodu içeren *guessing-game.py* adlı bir Python dosyası oluşturun:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Paketi `ptvsd` kullanarak ortamınıza `pip3 install ptvsd`yükleyin.
   >[!NOTE]
   >Sorun giderme için ihtiyacınız olması durumunda yüklenen ptvsd sürümünü kaydetmek iyi bir fikirdir; [ptvsd liste](https://pypi.python.org/pypi/ptvsd) de mevcut sürümlerini gösterir.

1. Diğer koddan *önce, guessing-game.py*mümkün olan en erken noktada aşağıdaki kodu ekleyerek uzaktan hata ayıklamayı etkinleştirin. (Katı bir gereklilik olmasa da, `enable_attach` işlev çağrılmadan önce oluşturulan arka plan iş parçacığı hata ayıklamak mümkün değildir.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Dosyayı kaydedin ve çalıştırın. `python3 guessing-game.py` Arka planda `enable_attach` çalışan arama ve programla etkileşimde bulunan çağrı, gelen bağlantıları bekler. İstenirse, hata ayıklama ekleyene kadar programı engellemek için `wait_for_attach` işlev sonra `enable_attach` çağrılabilir.

> [!Tip]
> Buna ek `enable_attach` `wait_for_attach`olarak ve , ptvsd `break_into_debugger`de yardımcı işlevi sağlar , hata ayıklayıcı bağlı ise programlı bir kesme noktası olarak hizmet vermektedir. Hata ayıklama `is_attached` ekliyse `True` döndüren bir işlev de vardır (diğer `ptvsd` işlevleri aramadan önce bu sonucu denetlemeye gerek olmadığını unutmayın).

## <a name="attach-remotely-from-python-tools"></a>Python Tools'tan uzaktan ekleme

Bu adımlarda, uzak işlemi durdurmak için basit bir kesme noktası belirleriz.

1. Uzak dosyanın bir kopyasını yerel bilgisayarda oluşturun ve Visual Studio'da açın. Dosyanın nerede bulunduğu önemli değildir, ancak adı uzak bilgisayardaki komut dosyasının adıyla eşleşmelidir.

1. (İsteğe bağlı) Yerel bilgisayarınızda ptvsd için IntelliSense olması için, Python ortamına ptvsd paketi yükleyin.

1. İşleme **Hata Ayıklama** > **Ekle'yi**seçin.

1. Görünen **İşleme Ekle** iletişim kutusunda, **Bağlantı Türünü** **Python remote (ptvsd)** olarak ayarlayın. (Visual Studio'nun eski sürümlerinde bu komutlar **Transport** ve **Python uzaktan hata ayıklama**olarak adlandırılır.)

1. Bağlantı **Hedefi** alanında (Eski sürümlerde `tcp://<ip_address>:5678` **Niteleyici),** uzak bilgisayarın (açık bir adres veya myvm.cloudapp.net gibi bir ad olabilir) nerede `<ip_address>` olduğunu ve `:5678` uzaktan hata ayıklama bağlantı noktası numarasıdır girin.

1. O bilgisayardaki kullanılabilir ptvsd işlemlerinin listesini doldurmak için **Enter** tuşuna basın:

    ![Bağlantı hedefini girme ve listeleme süreçlerini](media/remote-debugging-qualifier.png)

    Bu listeyi dolduran uzak bilgisayarda başka bir program başlattıysanız, **Yenile** düğmesini seçin.

1. Hata ayıklama işlemini seçin ve sonra **Ekle**veya işlemi çift tıklatın.

1. Visual Studio daha sonra komut dosyası uzak bilgisayarda çalıştırmaya devam ederken hata ayıklama moduna geçer ve her zamanki [hata ayıklama](debugging-python-in-visual-studio.md) özelliklerini sağlar. Örneğin, `if guess < number:` satırda bir kesme noktası ayarlayın, ardından uzak bilgisayara geçin ve başka bir tahmin girin. Bunu yaptıktan sonra, yerel bilgisayarınızdaki Visual Studio bu kesme noktasında durur, yerel değişkenleri gösterir ve benzeri devam eder:

    ![Visual Studio kesme noktası vurulduğunda hata ayıklama duraklatıyor](media/remote-debugging-breakpoint-hit.png)

1. Hata ayıklamayı durdurduğunuzda, Visual Studio uzak bilgisayarda çalıştırmaya devam eden programdan ayrılır. ptvsd de hata ayıklama takmak için dinlemeye devam ediyor, böylece istediğiniz zaman tekrar işleme takabilirsiniz.

### <a name="connection-troubleshooting"></a>Bağlantı sorun giderme

1. **Bağlantı Türü** için **Python remote (ptvsd)** seçtiğinizden emin olun (Python uzaktan **aktarım** için eski sürümlerle hata**ayıklama.)**
1. **Bağlantı Hedefi'ndeki** (veya **Eleme)** gizlinin uzak koddaki sırla tam olarak eşleşin.
1. **Bağlantı Hedefi'ndeki** (veya **Eleme)** IP adresinin uzak bilgisayarınkiyle eşleşip eşleşmediğini denetleyin.
1. Uzak bilgisayardaki uzak hata ayıklama bağlantı noktasını açıp açmadığınızı ve bağlantı hedefine bağlantı noktası sonekini `:5678`ekleyip dahil ettiğinizi kontrol edin.
    - Farklı bir bağlantı noktası kullanmanız gerekiyorsa, bağımsız `enable_attach` değişkeni `address` kullanarak çağrıda `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`belirtebilirsiniz. Bu durumda, güvenlik duvarındaki belirli bağlantı noktasını açın.
1. Aşağıdaki tabloda Visual Studio'da kullandığınız Python araçlarının `pip3 list` sürümü tarafından kullanılan eşleşmeler tarafından döndürülen uzak bilgisayara yüklenen ptvsd sürümünün olup olmadığını kontrol edin. Gerekirse, uzak bilgisayarda ptvsd güncelleyin.

    | Visual Studio sürüm | Python araçları/ptvsd sürümü |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (eski hata ayıklama: 3.2.1.0) |
    | 2017 15.7 | 4.1.1a1 (eski hata ayıklama: 3.2.1.0) |
    | 2017 15.4, 15.5, 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>ptvsd 3.x kullanma

Aşağıdaki bilgiler yalnızca ptvsd 4.x'te kaldırılan belirli özellikleri içeren ptvsd 3.x ile uzaktan hata ayıklama için geçerlidir.

1. ptvsd 3.x ile, `enable_attach` çalışan komut dosyasına erişimi kısıtlayan ilk bağımsız değişken olarak bir "gizli" geçmeniz gerekir. Uzaktan hata ayıklama takıldığında bu sırrı girersiniz. Önerilmese de, herkesin bağlanmasına, kullanmasına `enable_attach(secret=None)`izin verebilirsiniz.

1. Bağlantı hedef URL'si Python `enable_attach` kodunda geçirilen dize nerededir. `tcp://<secret>@<ip_address>:5678` `<secret>`

Varsayılan olarak, ptvsd 3.x uzaktan hata ayıklama sunucusuna bağlantı yalnızca gizli tarafından güvenli ve tüm veriler düz metin olarak geçirilir. Daha güvenli bir bağlantı için, ptvsd 3.x `tcsp` aşağıdaki gibi ayarladığınız protokolü kullanarak SSL'yi destekler:

1. Uzak bilgisayarda, openssl kullanarak ayrı kendi imzalı sertifika ve anahtar dosyaları oluşturun:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    İstendiğinde, openssl tarafından istendiğinde **Ortak Ad** için ana bilgisayar adını veya IP adresini (bağlanmak için hangisini kullanırsanız kullanın) kullanın.

    (Ek ayrıntılar için Python `ssl` modül dokümanlarında Kendi imzalı [sertifikalara](https://docs.python.org/3/library/ssl.html#self-signed-certificates) bakın. Bu dokümanlarda komutun yalnızca tek bir birleşik dosya oluşturduğunu unutmayın.)

1. Kodda, `enable_attach` çağrıyı dosya adlarını değerler olarak kullanmak `certfile` üzere `keyfile` ve bağımsız değişkenler içerecek şekilde `ssl.wrap_socket` değiştirin (bu bağımsız değişkenler standart Python işleviyle aynı anlama sahiptir):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Yerel bilgisayardaki kod dosyasında da aynı değişikliği yapabilirsiniz, ancak bu kod gerçekte çalışmadığından kesinlikle gerekli değildir.

1. Python programını uzak bilgisayarda yeniden başlatArak hata ayıklamaya hazır hale getirin.

1. Visual Studio ile Windows bilgisayarında Güvenilir Root CA'ya sertifika ekleyerek kanalı güvenli hale alın:

    1. Sertifika dosyasını uzak bilgisayardan yerel bilgisayara kopyalayın.
    1. **Denetim Masası'nı** açın ve **Yönetim Araçları** > Bilgisayar**Sertifikalarını Yönet'e**gidin.
    1. Görünen pencerede, sol **taraftaki Güvenilen Kök Sertifika Syon Larını** genişletin, **Sertifikalar'ı**sağ tıklatın ve **Tüm Görevler** > **Alma'yı**seçin.
    1. Uzak bilgisayardan kopyalanan *.cer* dosyasına gidin ve seçin, ardından içe aktarmayı tamamlamak için iletişim günlüklerini tıklatın.

1. Daha önce açıklandığı gibi Visual Studio'da `tcps://` ekleme işlemini, şimdi **Bağlantı Hedefi** (veya **Eleme)** için protokol olarak kullanarak yineleyin.

    ![SSL ile uzaktan hata ayıklama aktarımını seçme](media/remote-debugging-qualifier-ssl.png)

1. Visual Studio, SSL üzerinden bağlanırken olası sertifika sorunları hakkında sizi ister. Uyarıları yoksayabilir ve devam edebilirsiniz, ancak kanal hala gizlice dinlemeye karşı şifrelenmiş olsa da, ortadaki adam saldırılarına açık olabilir.

    1. **Uzaktan sertifikanın** aşağıda güvenilir bir uyarı olmadığını görürseniz, sertifikayı Güvenilir Kök CA'ya düzgün şekilde eklemediğiniz anlamına gelir. Bu adımları kontrol edin ve tekrar deneyin.

        ![SSL sertifikası güvenilir uyarı](media/remote-debugging-ssl-warning.png)

    1. Uzak sertifika adının aşağıdaki ana bilgisayar adı uyarısı ile **eşleşmediğini** görürseniz, sertifikayı oluştururken uygun ana bilgisayar adı veya IP adresini **Ortak Ad** olarak kullanmadığınız anlamına gelir.

        ![SSL sertifika ana bilgisayar adı uyarısı](media/remote-debugging-ssl-warning2.png)
