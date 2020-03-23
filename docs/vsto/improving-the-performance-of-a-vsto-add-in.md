---
title: VSTO Eklentisinin performansını artırmak
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416555"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>VSTO eklentisinin performansını artırmak
  Office uygulamaları için oluşturduğunuz VSTO Eklentilerini hızlı bir şekilde başlatmaları, kapatmaları, öğeleri açmaları ve diğer görevleri gerçekleştirmeleri için kullanıcılarınıza daha iyi bir deneyim sunabilirsiniz. VSTO Eklentiniz Outlook içinse, düşük performans nedeniyle VSTO Eklentinizin devre dışı bırakılma olasılığını da azaltabilirsiniz. Aşağıdaki stratejileri uygulayarak VSTO Eklentinizin performansını artırabilirsiniz:

- [VsTO Eklentilerini isteğe bağlı yükleyin.](#Load)

- [Windows Installer kullanarak Office çözümlerini yayımlayın.](#Publish)

- [Bypass Şerit yansıması](#Bypass).

- [Ayrı bir yürütme iş parçacığı nda pahalı işlemleri gerçekleştirin.](#Perform)

  Outlook VSTO Eklentisi'ni en iyi duruma getirme hakkında daha fazla bilgi [için, VSTO Eklentilerini etkin tutmak için Performans ölçütlerine](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)bakın.

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>VSTO Eklentilerini isteğe bağlı yükleyin
 VSTO Eklentisini yalnızca aşağıdaki koşullar altında yükleyecek şekilde yapılandırabilirsiniz:

- VSTO Eklentisi yüklendikten sonra kullanıcı uygulamayı ilk kez başlatın.

- Kullanıcı, uygulamayı sonraki bir zamanda başladıktan sonra VSTO Eklentisi ile ilk etkileşimde bulunun.

  Örneğin, kullanıcı **Verilerimi Al**etiketli özel bir düğme seçtiğinde VSTO Eklentiniz bir çalışma sayfasını verilerle doldurabilir. Uygulama, **Verilerimi Al** düğmesinin Şerit'te görünebilmeleri için VSTO Eklentinizi en az bir kez yüklemelidir. Ancak, kullanıcı uygulamayı bir sonraki sefere başlattığında VSTO Eklentisi yeniden yüklenmez. VSTO Eklentisi yalnızca kullanıcı **Verilerimi Al** düğmesini seçtiğinde yüklenir.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>VsTO Eklentilerini isteğe bağlı yüklemek için ClickOnce çözümlerini yapılandırmak için

1. **Çözüm Gezgini'nde**proje düğümlerini seçin.

2. Menü çubuğunda**Özellik Sayfalarını** **Görüntüle'yi** > seçin.

3. **Yayımla** sekmesinde **Seçenekler** düğmesini seçin.

4. Seçenekleri **Yayımla** iletişim kutusunda, **Office Ayarları** liste öğesini seçin, **İsteğe Yükle** seçeneğini seçin ve ardından **Tamam** düğmesini seçin.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>VsTO Eklentilerini isteğe bağlı yüklemek için bir Windows Installer çözümlerini yapılandırmak için

1. Kayıt defterinde, ** _Root_\Software\Microsoft\Office\\_ApplicationName_\Addins\\Add-in ID** anahtarının `LoadBehavior` girişini **0x10'a**ayarlayın.

     Daha fazla bilgi için [VSTO Eklentileri için Kayıt Defteri girişlerine](../vsto/registry-entries-for-vsto-add-ins.md)bakın.

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Çözümü hata ayıklarken VSTO Eklentilerini isteğe bağlı yüklemek için bir çözüm yapılandırmak için

1. `LoadBehavior` **0x10** ** _için Root_\Software\Microsoft\Office\\_ApplicationName_\Addins\\Add-in ID** anahtarının girişini ayarlayan bir komut dosyası oluşturun.

     Aşağıdaki kod bu komut dosyasının bir örneğini gösterir.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Komut dosyasını kullanarak kayıt defterini güncelleyen bir yapı sonrası olay oluşturun.

     Aşağıdaki kod, yapı sonrası olaya ekleyebileceğiniz bir komut dizeörneği gösterir.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     C# projesinde yapı sonrası olayın nasıl oluşturulabildiğini öğrenmek için bkz [&#35;&#41;&#40;. ](../ide/how-to-specify-build-events-csharp.md)

     Visual Basic projesinde yapı sonrası olayın nasıl oluşturulabildiğini öğrenmek için bkz [&#41;&#40;. ](../ide/how-to-specify-build-events-visual-basic.md)

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Windows Installer kullanarak Office çözümlerini yayımlama
 Çözümünüzü Windows Installer'ı kullanarak yayımlarsanız, Visual Studio 2010 Office çalışma zamanı araçları, VSTO Eklentisi yüklendiğinde aşağıdaki adımları atlar.

- Apaçık şema doğruluyor.

- Güncelleştirmeleri otomatik olarak denetler.

- Dağıtım bildirimlerinin dijital imzalarının doğrulanması.

  > [!NOTE]
  > VSTO Eklentinizi kullanıcıların bilgisayarlarında güvenli bir konuma dağıtırsanız bu yaklaşım gerekli değildir.

  Daha fazla bilgi için bkz. Windows [Installer'ı kullanarak Bir Office çözümlerini dağıtın.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Bypass Şerit yansıması
 Kullanarak bir çözüm [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]oluşturursanız, çözüm dağıtTığınızda kullanıcılarınızın Visual Studio 2010 Tools for Office çalışma zamanının en son sürümünü yüklediğinden emin olun. VSTO çalışma zamanının eski sürümleri, Şerit özelleştirmelerini bulmak için çözüm derlemelerine yansıtılır. Bu işlem VSTO Eklentisinin daha yavaş yüklenmesine neden olabilir.

 Alternatif olarak, Visual Studio 2010 Office çalışma zamanı için araçlar sürümünün Şerit özelleştirmelerini tanımlamak için yansımayı kullanmasını engelleyebilirsiniz. Bu stratejiyi `CreateRibbonExtensibility` izlemek için yöntemi geçersiz kılın ve Şerit nesnelerini açıkça döndürün. VSTO Eklentiniz şerit özelleştirmesi içermiyorsa, `null` yöntemin içine dönün.

 Aşağıdaki örnek, bir alanın değerini temel alan bir Şerit nesnesi döndürür.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Ayrı bir yürütme iş parçacığında pahalı işlemler gerçekleştirme
 Ayrı bir iş parçacığında zaman alan görevleri (uzun çalışan görevler, veritabanı bağlantıları veya diğer ağ çağrıları gibi) gerçekleştirmeyi düşünün. Daha fazla bilgi için [Office'te İş Parçacığı desteğine](../vsto/threading-support-in-office.md)bakın.

> [!NOTE]
> Office nesnesi modeline çağıran tüm kodlar ana iş parçacığında yürütülmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Talep yükleme VSTO Eklentileri](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Office Eklentilerinde CLR'yi geciktirme](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Visual Studio kullanarak Office için VSTO Eklentileri oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)
