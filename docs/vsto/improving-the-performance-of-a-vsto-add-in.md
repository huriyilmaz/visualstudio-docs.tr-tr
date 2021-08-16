---
title: VSTO Eklentinin performansını geliştirme
description: Office uygulamaları için VSTO, kapatacak, öğeleri açacak ve diğer görevleri gerçekleştirecek şekilde, bu eklentileri iyileştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 669e690059acb6854eceee224b5439e07c08072d26ba08b3aa69c7fab0a8fe0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267734"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Bir eklentinin VSTO geliştirme
  Office uygulamaları için VSTO eklentileri en iyi duruma getirerek kullanıcılarınıza daha iyi bir deneyim sabilirsiniz. Böylece, öğeleri hızla başlatacak, kapatacak, öğeleri açabilir ve diğer görevleri gerçekleştirebilirler. Eklentiniz VSTO içinse, Outlook performansın düşük olması nedeniyle VSTO Eklentinizin devre dışı olma şansını da azaltabilirsiniz. Aşağıdaki stratejileri kullanarak VSTO eklentinizin performansını artırabilirsiniz:

- [isteğe VSTO eklentilerini yükleme.](#Load)

- [Office Yükleyicisi'Windows yayımlayın.](#Publish)

- [Şerit yansımasını atla.](#Bypass)

- [Ayrı bir yürütme iş parçacığında pahalı işlemler gerçekleştirin.](#Perform)

  Bir eklentinin nasıl en iyi duruma Outlook VSTO için bkz. Eklentilerin etkin VSTO [performans ölçütleri.](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>VSTO eklentilerini isteğe bağlı olarak yükleme
 Bir eklentiyi VSTO yüklemek için yalnızca aşağıdaki durumlarda yapılandırın:

- Kullanıcı, eklenti yüklendikten sonra uygulamayı VSTO ilk kez başlatır.

- Kullanıcı uygulamayla ilk kez etkileşime VSTO sonra eklentiyi ekler.

  Örneğin, VSTO Veri Al etiketli özel bir düğmeyi seçen kullanıcı çalışma sayfasını verilerle doldurmak için VSTO **Eklentiniz olabilir.** Uygulamanın, VSTO Al düğmesinin Şerit'te görünmesi için  eklentinizi en az bir kez yüklemesi gerekir. Ancak, VSTO kullanıcı uygulamayı bir sonraki sefer başlatırsa eklenti yeniden yüklenmez. VSTO Eklenti, yalnızca kullanıcı Verilerimi Al düğmesini **seçerken** yüklenir.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Bir ClickOnce isteğe bağlı VSTO yük dengeleme çözümü yapılandırmak için

1. Bu **Çözüm Gezgini** proje düğümünü seçin.

2. Menü çubuğunda Özellik Sayfalarını **Görüntüle'yi**  >  **seçin.**

3. Yayımla **sekmesinde** Seçenekler **düğmesini** seçin.

4. Yayımlama **Seçenekleri iletişim** kutusunda,  Office Ayarlar listesi öğesini seçin, isteğe bağlı yükle seçeneğini **belirleyin** ve ardından Tamam **düğmesini** seçin.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Bir Windows Yükleyicisi çözümünü isteğe bağlı VSTO yüklemesi için

1. Kayıt defterinde Root `LoadBehavior` **\Software\Microsoft\Office \\ _ApplicationName_\Addins Eklenti \\ _Kimliği_** anahtarının girişini 0x10. 

     Daha fazla bilgi için [bkz. Eklentilerini VSTO kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Çözümü, çözümde hata VSTO eklentilerini isteğe bağlı olarak yük dengelemek üzere yapılandırmak için

1. `LoadBehavior` **_Root_\Software\Microsoft\Office \\ _ApplicationName_\Addins Eklenti \\ _Kimliği_** anahtarının girişini 0x10. 

     Aşağıdaki kod, bu betiğin bir örneğini gösterir.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Betiği kullanarak kayıt defterini güncelleştirmeye devam etmek için derleme sonrası bir olay oluşturun.

     Aşağıdaki kod, derleme sonrası bir olayına ekleyebilirsiniz bir komut dizesi örneğini gösterir.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Bir C# projesinde derleme sonrası olay oluşturma hakkında daha fazla bilgi için bkz. Nasıl [2019'da derleme olayları &#40;C&#35;&#41;. ](../ide/how-to-specify-build-events-csharp.md)

     Bir derleme projesinde derleme sonrası olay oluşturma hakkında bilgi Visual Basic [bkz. Nasıl &#40;Visual Basic&#41;. ](../ide/how-to-specify-build-events-visual-basic.md)

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Office Yükleyicisi'Windows çözümleri yayımlama
 Windows Yükleyicisi'Windows yayımlarsanız, Office çalışma zamanı için Visual Studio 2010 Araçları, VSTO Eklenti yüklenirken aşağıdaki adımları atlar.

- Bildirim şemasını doğrulama.

- Güncelleştirmeleri otomatik olarak denetleme.

- Dağıtım bildirimlerinin dijital imzalarını doğrulama.

  > [!NOTE]
  > Eklentinizi kullanıcıların bilgisayarlarında güvenli bir VSTO dağıtmak için bu yaklaşım gerekli değildir.

  Daha fazla bilgi için [bkz. Office Yükleyicisi kullanarak bir Windows dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Şerit yansımasını atlama
 kullanarak bir çözüm derlemeniz, çözümü dağıtırken kullanıcılarınızı Office çalışma zamanı için Visual Studio 2010 Araçları'nın en son sürümünü yüklemiş [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] olduğundan emin olun. VSTO çalışma zamanının eski sürümleri, Şerit özelleştirmelerini bulmak için çözüm derlemelerine yansıtıldı. Bu işlem, eklentinin VSTO yavaş yüklemesi için neden olabilir.

 Alternatif olarak, Office çalışma zamanı için Visual Studio 2010 Araçları'nın herhangi bir sürümünün Şerit özelleştirmelerini tanımlamak için yansıma kullanmasını önleyebilirsiniz. Bu stratejiyi takip etmek için yöntemini `CreateRibbonExtensibility` geçersiz kılın ve Şerit nesnelerini açıkça iade edin. VSTO Eklentiniz Şerit özelleştirmesi içeriyorsa `null` yönteminin içine geri döner.

 Aşağıdaki örnek, bir alanın değerine göre bir Şerit nesnesi döndürür.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs" id="Snippet1":::

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Ayrı bir yürütme iş parçacığında pahalı işlemler gerçekleştirme
 Ayrı bir iş parçacığında zaman alan görevler (uzun süre çalışan görevler, veritabanı bağlantıları veya diğer ağ çağrıları gibi) gerçekleştirmeyi göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Office.](../vsto/threading-support-in-office.md)

> [!NOTE]
> Nesne modeline çağrı Office tüm kodun ana iş parçacığında yürütmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Eklentilerde VSTO yükleme](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Ek Eklentilerde CLR'Office gecikmeli yükleme](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Visual Studio kullanarak Office için VSTO Eklentileri oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)