---
title: Command-Line Yakalama Aracı | Microsoft Docs
description: Tüm özellik DXCap.exe Direct3D 10 ile Direct3D 12'yi destekleyen grafik tanılama yakalama ve kayıttan yürütmeye yönelik bir komut satırı aracı olan DXCap.exe hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ace21b9e639f78c022c03825623f6c7d5190911d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626462"
---
# <a name="command-line-capture-tool"></a>Komut Satırı Yakalama Aracı
DXCap.exe, grafik tanılama yakalama ve kayıttan yürütme için bir komut satırı aracıdır. Tüm özellik düzeylerinde Direct3D 10 ile Direct3D 12 arasında bir destek sağlar.

## <a name="syntax"></a>Sözdizimi

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>Parametreler
 `-file``filename`Yakalama modu ( `-c` ) `filename` altında, grafik bilgilerini kaydeden grafik günlüğü dosyasının adını belirtir. `filename`Belirtilmezse, grafik bilgileri varsayılan olarak adlı bir dosyaya `<appname>-<date>-<time>.vsglog` kaydedilir.

 Doğrulama (-v) `filename` modu altında, doğrulanması gereken grafik günlüğü dosyasının adını belirtir. `filename`Belirtilmezse, son doğrulanmış grafik günlüğü yeniden kullanılır.

 `-frame``frames`Yakalama modu `frames` altında, yakalamak istediğiniz kareleri belirtir. İlk kare 1'tir. Virgül ve aralıklar kullanarak birkaç kare belirtebilirsiniz. Örneğin, ise `frames` , , , , ve `2, 5, 7-9, 15` `2` `5` `7` `8` `9` çerçeveleri `15` yakalanır.

> [!TIP]
> Yazdırma `-frame` `manual` Ekranı tuşuna basılarak karelerin el ile yakalanacaklarını belirtmek için kullanın. Uygulama başlatıldığında kareler yakalanır; çerçeveleri yakalamayı durdurmak için komut satırı arabirimine dönüp Enter tuşuna basın.

 `-period``periods`Yakalama modu `periods` altında, kareleri yakalamak istediğiniz süre aralıklarını saniyeler içinde belirtir. Virgül ve aralıklar kullanarak birkaç nokta belirtebilirsiniz. Örneğin , `periods` ise `2.1-5, 7.0-9.3` ile saniyeler arasında işlenen `2.1` `5` kareler ve ile saniyeler `7` arasında `9.3` yakalanır.

 `-c``app`[ `args...` ] Yakalama modu. Yakalama modu altında, grafik bilgilerini yakalamak istediğiniz uygulamanın adını belirtir; bu uygulamaya ek komut `app` `args...` satırı parametrelerini belirtir.

 `-p` [ `filename` ] Kayıttan yürütme modu ( `-p` ). Kayıttan yürütme `filename` modu altında, yeniden oynatacak grafik günlüğü dosyasının adını belirtir. `filename`Belirtilmezse, en son yeniden oynanmış grafik günlüğü yeniden kullanılır.

 `-debug` Kayıttan yürütme modu `-debug` altında, direct3D hata ayıklama katmanı etkinken kayıttan yürütmenin oynat gerektiğini belirtir.

 `-warp` Kayıttan yürütme modu `-warp` altında, PLAYBACK yazılım işleyicisi kullanılarak kayıttan yürütmenin oynatılacak olduğunu belirtir.

 `-hw` Kayıttan yürütme modu `-hw` altında, kayıttan yürütmenin GPU donanımı kullanılarak oynat gerektiğini belirtir.

 `-config` Kayıttan yürütme `-config` modu altında, grafik günlük dosyasını yakalamak için kullanılan makineyle ilgili tüm bilgileri görüntüler.

 `-rawmode` Kayıttan yürütme modu `-rawmode` altında, kayıttan yürütmenin kayıtlı olaylarda değişiklik yapmadan gerçekleştirilecek olduğunu belirtir. Normal çalışma altında kayıttan yürütme modu, hata ayıklamayı basitleştirmek ve kayıttan yürütmeyi hızlandırmak için kayıttan yürütmede küçük değişikliklere neden olabilir. Örneğin, değiştirme zinciri komutlarını yürütmek yerine değiştirme zinciri çıkışının benzetimini gerçekleştiriyor olabilir. Genellikle bu kayıttan yürütme bir sorun değildir, ancak kayıttan yürütmenin kaydedilen olay için daha fazla güvenilir olacak şekilde gerçekleşmesi gerekir. Örneğin, tam ekran işleme davranışını tam ekran modunda çalışırken yakalanan bir uygulamaya geri yüklemek için bu seçeneği kullanabilirsiniz.

 `-toXML` [ `xml_filename` ] Kayıttan yürütme `xml_filename` modunda, kayıttan yürütmenin XML gösteriminin yazıldığı dosyanın adını belirtir. Belirtilmezse, XML gösterimi, geri çalınan dosyayla aynı adlı bir dosyaya `xml_filename` yazılır, ancak bir uzantı `.xml` verilir.

 `-v` Doğrulama modu. Doğrulama modunda yakalanan kareler hem donanımda hem de OSP'de geri çalınır ve sonuçları bir görüntü karşılaştırma işlevi kullanılarak karşılaştırıldı. İşlemenizi etkileyen sürücü sorunlarını hızla belirlemek için bu özelliği kullanabilirsiniz.

 `-examine``events`Doğrulama modu `events` altında, anlık sonuçları karşılaştıran grafik olaylarını belirtir. Örneğin, `-examine present,draw,copy,clear` karşılaştırmayı yalnızca bu kategorilere ait olaylarla sınırlar.

> [!TIP]
> Ile başlamanız önerilir çünkü bu çoğu sorunu ortaya çıkaracak ancak daha kapsamlı bir olay `-examine present,draw,copy,clear` kümesinden çok daha kısa bir süre alır. Gerekirse, bu olayları doğrulamak ve diğer tür sorunları ortaya çıkarmak için daha büyük veya farklı bir olay kümesi belirtabilirsiniz.

 `-haltonfail` Doğrulama modu altında, `-haltonfail` donanım ve RENDER oluşturucu arasındaki farklar algılandığında doğrulamayı durdurduğu. Bir tuşa basıldığında doğrulama devam eder.

 `-exitonfail` Doğrulama modu altında, `-exitonfail` donanım ile RENDER oluşturucu arasında farklar algılandığında doğrulamadan hemen çıkar. Program bu şekilde çıkarsa ortama geri döner; aksi `0` takdirde `1` döndürür.

 `-showprogress` Doğrulama modu altında, `-showprogress` doğrulama oturumuyla ilgili ilerleme bilgilerini görüntüler. LEFT ilerleme durumu solda görüntülenir; donanım ilerleme durumu sağda görüntülenir.

 `-e``search_string`Yüklü UWP uygulamalarını numaralar. UWP uygulamalarıyla komut satırı yakalamaları gerçekleştirmek için bu bilgileri kullanabilirsiniz.

 `-info` Makine ve yakalama URL'leri hakkında bilgileri görüntüler.

## <a name="remarks"></a>Açıklamalar
 DXCap.exe üç modda çalışır:

 Yakalama modu (-c) Çalışan bir uygulamanın grafik bilgilerini yakalama ve grafik günlük dosyasına kaydetme. Yakalama özellikleri ve dosya biçimi, veri yakalama özellikleriyle Visual Studio.

 Kayıttan yürütme modu (-p) Var olan bir grafik günlüğü dosyasından daha önce yakalanan grafik olaylarını kayıttan yürütme. Varsayılan olarak, grafik günlük dosyası tam ekran uygulamasından yakalansa bile kayıttan yürütme bir pencerede gerçekleşir. Kayıttan yürütme yalnızca grafik günlüğü dosyası tam ekran uygulamasından yakalanır ve belirtilirken tam `-rawmode` ekranda gerçekleşir.

 Doğrulama modu ( ) Yakalanan kareleri hem donanımda hem de IMAGE'de tekrar çalarak ve ardından bir görüntü karşılaştırma işlevi kullanarak sonuçlarını karşılaştırarak `-v` işleme davranışını doğrular. İşlemenizi etkileyen sürücü sorunlarını hızla belirlemek için bu özelliği kullanabilirsiniz.

 Bu modlara ek olarak dxcap.exe, grafik bilgilerini yakalama veya kayıttan yürütme gerçekleştirmez diğer iki işlevi gerçekleştirir.

 Numaralama işlevi ( `-e` ) Makinede yüklü olan UWP uygulamalarıyla ilgili ayrıntıları görüntüler. Bu ayrıntılar, UWP uygulamasında yürütülebilir dosyayı tanımlamak için paket adını ve appid'i içerir. DXCap.exe kullanarak bir Windows Mağazası uygulamasından grafik bilgilerini yakalamak için, bir masaüstü uygulamasını yakalarken kullanılan yürütülebilir dosya adı yerine paket adını ve appid'yi kullanın.

 Info işlevi ( `-info)` Makine ve yakalama URL'leri ile ilgili ayrıntıları görüntüler.

## <a name="examples"></a>Örnekler

### <a name="capture-graphics-information-from-a-desktop-app"></a>Masaüstü uygulamasından grafik bilgilerini yakalama
 Grafik `-c` bilgilerini yakalamak istediğiniz uygulamayı belirtmek için kullanın.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Varsayılan olarak, grafik bilgileri adlı bir dosyaya `<appname>-<date>-<time>.vsglog` kaydedilir. Kaydedilen `-file` farklı bir dosya belirtmek için kullanın.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Uygulamanın dosya adı sonrasında dahil etmek üzere, yakalanan uygulamaya ek komut satırı parametreleri belirtin.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Yukarıdaki örnekteki komut, Internet Explorer'nin masaüstü sürümünden grafik bilgilerini yakalarken www.fishgl.com web sayfasını görüntüler ve 3-B içeriği işlemek için WebGL API'sini kullanır.

> [!NOTE]
> Uygulama geçirildikten sonra görünen komut satırı bağımsız değişkenleri olduğundan, seçeneğini kullanmadan önce DXCap.exe için DXCap.exe bağımsız değişkenleri belirtmeniz `-c` gerekir.

### <a name="capture-graphics-information-from-a-uwp-app"></a>UWP uygulamasından grafik bilgilerini yakalama.
 Bir UWP uygulamasından grafik bilgilerini yakaabilirsiniz.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Bir UWP uygulamasından yakalamak için DXCap.exe kullanmak, Windows masaüstü uygulamasından yakalamak için kullanmaya benzer, ancak bir masaüstü uygulamasını dosya adına göre tanımlamak yerine, bir UWP uygulamasını paket adına ve yakalamak istediğiniz paketin içindeki yürütülebilir dosyanın adına veya kimliğine göre tanımlayabilirsiniz. Makinenize yüklenmiş olan UWP uygulamalarını tanımlamayı daha kolay hale DXCap.exe seçeneğini kullanarak `-e` bunları numaralandırabilirsiniz:

```cmd
DXCap.exe -e
```

 İsteğe bağlı bir arama dizesi sarak, aramakta olduğunuz uygulamayı buluabilirsiniz. Arama dizesi sağlanıyorsa, DXCap.exe adı, uygulama adı veya uygulama kimlikleri arama dizesiyle aynı olan UWP uygulamalarını numaralar. Arama büyük/büyük/büyük harfe duyarlı değildir.

```cmd
DXCap.exe -e map
```

 Yukarıdaki komut, "map" ile eşleni UWP uygulamalarını numaralar; çıktısı şu şekildedir:

 **Paket "Microsoft.BingMaps":** **InstallDirectory: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **FullName : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID : S-1-5-21-212752184-1604012920-1887927527-5603533 Adı:** **Microsoft.BingMaps** Publisher : **CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** Version : **2.1.2914.1734** **Launchable Applications:** **Id: AppexMaps** **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec (başlatmak için): DXCap.exe -c Microsoft.BingMaps_2 DXCap.exe.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** Numaralandı her uygulamanın son çıktı satırı, grafik bilgilerini yakalamak için kullanabileceğiniz komutu görüntüler.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Belirli kareleri veya kareleri belirli zamanlar arasında yakalama.
 Virgül `-frame` ve aralık kullanarak yakalamak istediğiniz kareleri belirtmek için kullanın:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 Veya `-period` çerçevelerin yakalanması için bir zaman aralığı kümesi belirtmek için kullanın. Zaman aralıkları saniyeler içinde belirtilir ve birden çok aralık belirtilebilir:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Kareleri etkileşimli olarak yakalama.
 Çerçeveleri `-manual` etkileşimli olarak yakalamak için kullanın. Yakalamayı başlatmak için Enter tuşuna basın ve durdurmak için Enter tuşuna tekrar basın.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Grafik günlük dosyasını geri oynatma
 Daha `-p` önce yakalanan grafik günlüğü dosyasını oynatmak için kullanın.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 En son yakalanan grafik günlüğünü oynatmak için dosya adını dışarıda bırakın.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Ham modda yeniden oynatma
 Yakalanan `-rawmode` komutları tam olarak gerçekleştikleri gibi oynatmak için kullanın. Normal kayıttan yürütmenin altında bazı komutlar öykünülmektedir; örneğin, tam ekran uygulamasından yakalanan grafik günlük dosyası bir pencerede yürütülecek; ham modu etkin olduğunda, aynı dosya tam ekranda yeniden oynatmayı dener.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>BILGISAYAR VEYA donanım cihazı kullanarak geri oynatma
 Donanım cihazında yakalanan grafik günlüğü dosyasını ZORLA YÜRÜTMEye veya DONANıM cihazında yakalanan bir günlüğün kayıttan yürütmeye zorlanır. `-warp`BACK kullanarak oynatmak için kullanın.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Donanım `-hw` kullanarak geri oynatmak için kullanın.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Grafik günlük dosyasını ATF'ye karşı doğrulama
 Doğrulama modu altında grafik günlüğü dosyası hem donanım hem de BILGISAYAR üzerinde geri çalınır ve sonuçları karşılaştırıldı. Bu, sürücüden kaynaklanan işleme hatalarını tanımlamanıza yardımcı olabilir. GRAFIK donanımının DOĞRU davranışını DOĞRULAMAK için -v kullanın.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Karşılaştırma miktarını azaltmak için, karşılaştırma için doğrulama komutlarının bir alt kümesini belirtebilirsiniz ve diğer komutlar yoksayılır. Sonuçlarını karşılaştırmak istediğiniz komutları belirtmek için -examine kullanın.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Grafik Günlüğü dosyasını PNG'lere dönüştürme
 Bir grafik günlük dosyasından kareleri görüntülemek veya analiz etmek DXCap.exe, yakalanan kareleri .png (Taşınabilir Ağ Grafikleri) görüntü dosyaları olarak kaydedebilir. Yakalanan `-screenshot` kareleri kayıttan yürütme modu altında kullanmak için .png kullanın.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Çıkışını `-frame` `-screenshot` yapmak istediğiniz kareleri belirtmek için ile kullanın.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Grafik Günlüğü dosyasını XML'ye dönüştürme
 FindStr veya XSLT gibi tanıdık araçları kullanarak grafik günlüklerini DXCap.exe analiz etmek için grafik günlük dosyasını XML'e dönüştürebilirsiniz. Kayıttan `-toXML` yürütme modu altında kullanarak günlüğü yeniden oynatmak yerine XML'ye dönüştürebilirsiniz.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Varsayılan olarak, XML çıkışı grafik günlüğüyle aynı adla bir dosyaya yazılır, ancak bu dosyaya bir .xml verilir. Yukarıdaki örnekte, XML dosyası **regression_test_12.xml.** XML dosyasına farklı bir ad vermek için sonrasında `-toXML` belirtin.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 Sonuçta elde edilen dosya, aşağıdakine benzer bir XML içerir:

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>Gereksinimler