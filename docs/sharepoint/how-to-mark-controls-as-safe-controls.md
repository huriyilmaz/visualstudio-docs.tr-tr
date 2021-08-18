---
title: 'Nasıl |: Denetimleri Kasa Olarak İşaret | Microsoft Docs'
description: Bir derlemeyi eklerken, Kasa proje öğesinin SharePoint Denetim Girişleri özelliğinde veya Paket Tasarımcısı'nda denetimleri güvenli denetim olarak işaretle.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e96a27be0ae8a71125964e27da99270d9142886c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092988"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Nasıllı: Denetimleri güvenli denetimler olarak işaretleme
  Güvenlik için SharePoint, betik eklemeye karşı korunan Web denetimleri ile korunmaz Web denetimleri arasında ayrımlar sağlar. Korumalı denetimlere *veya güvenli denetimlere* güvenilmeyen kullanıcılar tarafından erişilebilir. Denetimleri bir SharePoint proje öğesinin Kasa Denetim Girişleri özelliğinde veya pakete bir  derleme eklerken Paket Tasarımcısı'nda güvenli olarak işaretebilirsiniz. Daha fazla bilgi için bkz.

- [web.config Denetim Ayarlar Web](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) Bölümü [Derlemesini](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))Değiştirme ve Kaydetme Kasa.

> [!IMPORTANT]
> Bu yordamlar, açıklayıcı amaçlara yöneliktir. Yalnızca güvenli olduklarının emin olduğunuz durumlarda denetimleri güvenli olarak işaretle.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Kasa Denetim Girişleri Özelliğinde Kasa Denetimlerini İşaretleme

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Denetimleri güvenli denetim girdileri özelliğinde güvenli veya güvenli değil olarak işaretlemek için

1. Görsel Web SharePoint projesiyle bir çözüm oluşturun.

2. Web parçasına iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla TextBox1 ve Button1 varsayılan değerlerinde bırakın.

3. Web bölümü denetim girdisi özelliğine **iki Kasa ekleyin.** Bunu yapmak için, Özellikler penceresinde ASP.NET Denetim Girişleri ![özelliğinin](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")yanındaki üç nokta ( **Kasa ASP.NET** Mobil Tasarımcı üç nokta ) **düğmesini** seçin.

     Kasa **Denetim Girişleri iletişim** kutusu görüntülenir.

4. Denetim **Kasa iletişim** kutusunda, Üyeler bölmesine  iki güvenli denetim girişi eklemek için  Ekle düğmesini iki kez seçin: biri düğme, biri metin kutusu için.

5. İlk güvenli denetim girişini seçin ve ardından **Kasa** özelliğinin değerini **False,** Type **Name** özelliğini **Button1** olarak ve Kasa **Against Script** özelliğini False olarak **değiştirir.**

     Bu adım, düğme denetimlerini güvenli olmayan bir denetim olarak tanımlar.

6. Listede ikinci güvenli denetim girişini seçin. **Kasa özelliğinin** değerini **True** olarak bırakın ve **Type Name** özelliğini **TextBox1,** **Kasa Against Script** özelliğini True olarak **ayarlayın.**

     Metin kutusu denetimi artık betik eklemeye karşı güvenli bir denetim olarak işaretlenir.

7. İletişim **kutusunu kapatmak** için Tamam düğmesini seçin.

## <a name="marking-safe-controls-in-the-package-designer"></a>Paket Kasa Denetimlerini İşaretleme

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Denetimleri Paket Tasarımcısı'nda güvenli veya güvenli değil olarak işaretlemek için

1. Görsel Web SharePoint projesiyle bir çözüm oluşturun.

2. Web parçasına iki denetim ekleyin: metin kutusu ve düğme. Adları sırasıyla TextBox1 ve Button1 varsayılan değerlerinde bırakın.

     Denetimin ad alanını not almak için daha sonra kullanacağız.

3. Projeyi derlemek için menü çubuğunda **Derleme**  >  **Çözümü'ne** tıklayın.

4. Başka bir SharePoint oluşturun.

5. Bu **Çözüm Gezgini** *Package.Package* dosyasının kısayol menüsünü açın ve ardından  Aç'ı seçen Paket **Tasarımcısı'ni açın.**

6. Paket **Tasarımcısı'nda** Gelişmiş **sekmesini** seçin.

7. Ek **Derlemeler altında** Ekle düğmesini **seçin** ve ardından listeden Var **Olan Derlemeyi Ekle'yi** seçin.

8. Var Olan **Derleme Ekle iletişim** kutusunda, Kaynak Yolu'ASP.NET yanındaki üç noktayı ( Mobil Tasarımcı üç nokta ) düğmesini **seçin.**![](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")

9. 1. Adımda oluşturduğunuz SharePoint çözümünden derlemeyi seçin ve ardından Aç **düğmesini** seçin.

10. Bu örnekte Dağıtım Hedefi **seçeneğini** GlobalAssemblyCache olarak bırakın.

     Bu adım derlemenin sistem Genel Derleme Önbelleği'ne (GAC) dağıtımına neden olur. Derlemenin Web uygulaması (Bin) klasörüne dağıtması için bu seçeneği belirleyin. Daha fazla bilgi için [bkz. Web Bölümleri Foundation'SharePoint dağıtma.](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))

11. Denetimler **Kasa yeni** bir öğe **eklemek için buraya tıklayın düğmesini** seçin.

12. Aşağıdaki tabloda yer alan özelliklerin değerlerini girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetimin tam ad alanı, örneğin: **BdcModelProject1.VisualWebPart1.**|
    |Tür Adı|Düğme1|
    |Derleme Adı|Güçlü bir derleme adı, örneğin: Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Kasa|Kasa **kutusunun** işaretini kaldırın.|
    |Kasa Betikle Karşı|Komut Kasa **Karşı onay** kutusunu boş bırakın.|

    > [!NOTE]
    > Paket **Tasarımcısı'nın** Gelişmiş sekmesi  aracılığıyla eklenen  derlemeler için Derleme Adı değeri bir belirteç olamaz, kesin adlandırılmış bir derleme olması gerekir. Daha fazla bilgi için, [bkz. Creating and Using Strong-Named Derlemeleri](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Başka bir **güvenli** denetim girişi oluşturmak için Sekme tuşuna basın.

14. Yeni öğe **eklemek için buraya tıklayın düğmesini yeniden** seçin.

15. Aşağıdaki tabloda yer alan özelliklerin değerlerini girin.

    |Özellik Adı|Değer|
    |-------------------|-----------|
    |Ad Alanı|Denetimin tam ad alanı, örneğin: **BdcModelProject1.VisualWebPart1.**|
    |Tür Adı|TextBox1|
    |Derleme Adı|Güçlü bir derleme adı, örneğin: Microsoft. Office. SharePoint. ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Kasa|Veri **Kasa** kutusunu seçin.|
    |Kasa Betikle Karşı|Komut Kasa **Karşı Onay** kutusunu seçin.|

16. Sekme **tuşuna** basın ve iletişim **kutusunu kapatmak** için Tamam düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerinde paketleme ve dağıtım bilgilerini sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Paket ve dağıtım SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
