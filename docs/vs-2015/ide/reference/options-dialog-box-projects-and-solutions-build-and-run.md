---
title: Seçenekler Iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655184"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusunda, aynı anda oluşturulabilecek en fazla görsel C++ veya görsel C# proje sayısını, belirli varsayılan derleme davranışlarını ve bazı derleme günlüğü ayarlarını belirtebilirsiniz. **Seçenekler** iletişim kutusunu açmak için menü çubuğunda **Araçlar**, **Seçenekler** ' i seçin. Bu seçenek kümesine erişmek için **Projeler ve çözümler**' i genişletin ve ardından **Oluştur ve Çalıştır**' ı seçin.

## <a name="uielement-list"></a>UIElement Listesi
 **en fazla paralel proje derlemesi sayısı** Aynı anda oluşturulabilecek en fazla görsel C++ ve görsel C# proje sayısını belirtir. Yapı işlemini iyileştirmek için, en fazla paralel proje derleme sayısı, bilgisayarınızın CPU sayısına otomatik olarak ayarlanır. Maksimum değer 32 ' dir.

 **Çalıştırma sırasında yalnızca başlangıç projelerini ve bağımlılıklarını oluşturun** F5 tuşunu seçtiğinizde, bu onay kutusu seçiliyse yalnızca başlangıç projesi ve bağımlılıkları oluşturulur. **Hata Ayıkla**, menü çubuğundan **başla** ' yı seçin; ya da **menü çubuğunda Oluştur,** **Oluştur** ' u seçin. F5 tuşunu seçtiğinizde bu onay kutusu silinirse tüm projeler, bağımlılıklar ve çözüm dosyaları oluşturulur. **Hata Ayıkla**, menü çubuğundan **başla** ' yı seçin; ya da **menü çubuğunda Oluştur,** **Oluştur** ' u seçin. Varsayılan olarak, bu seçenek temizlenir.

 **Çalıştırıldığında, projeler güncel olmadığında**
 > [!NOTE]
> Bu liste yalnızca [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projelerine yöneliktir.

 Varsayılan olarak, F5 tuşunu veya **Hata Ayıkla** **' yı** seçtiğinizde menü çubuğunda bir proje yapılandırması güncel değilse bir ileti görüntülenir. Projenin yine de oluşturulup oluşturulmayacağını ve iletinin görüntülenip görüntülenmeyeceğini belirtebilirsiniz. İletinin görüntülenip görüntülenmeyeceğini ve ileti görünmüyorsa derleme davranışının ne olması gerektiğini belirtmek için bu seçeneği kullanın.

 **Her zaman oluştur** İleti kutusu görünmez ve proje, güncel olmayan yapılandırmaya rağmen oluşturulur. Bu seçenek, iletideki bu iletişim kutusunu bir **daha gösterme** kutusunu seçip **Evet** düğmesini seçerek ayarlanır.

 **Hiç derleme** İleti kutusu görünmez ve proje derlenmez. Bu seçenek, iletideki bu iletişim kutusunu bir **daha gösterme** kutusunu seçtiğinizde ayarlanır ve ardından **Hayır** düğmesini seçin.

 **Derlemek Için sor** Bir proje yapılandırmasının güncel olmadığı her seferinde ileti kutusunu görüntüler.

 **Çalıştırıldığında, derleme veya dağıtım hataları oluştuğunda** **Derleme menüsünden bir** derlemeyi başlattığınızda derleme hataları oluşursa, bir ileti görüntülenir. Uygulamayı başlatarak devam edip etmediğini ve her derleme hatası oluştuğunda iletinin görüntülenip görüntülenmeyeceğini belirtebilirsiniz. İletinin görüntülenip görüntülenmeyeceğini ve iletinin görünmeyeceğini belirten davranışı belirtmek için bu seçeneği kullanın.

> [!NOTE]
> Bu seçenek yalnızca [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projelerine yöneliktir.

 **Başlatmak Için sor** Derleme hataları her gerçekleştiğinde bir ileti kutusu görüntüler.

 **Başlatma** İleti kutusu görünmez ve uygulama başlatılmaz. Bu seçenek, ileti kutusunda **Bu iletişim kutusunu bir daha gösterme** onay kutusunu seçtiğinizde ayarlanır ve ardından **Hayır** düğmesini seçin.

 **Eski sürümü Başlat** İleti kutusu görünmez ve uygulamanın yeni oluşturulan sürümü başlatılmaz. Bu seçenek, ileti kutusunda **Bu iletişim kutusunu bir daha gösterme** onay kutusunu seçip **Evet** düğmesini seçerek ayarlanır.

 **Yeni çözümler için, seçili olan projeyi başlangıç projesi olarak kullanın** Bu onay kutusu işaretliyse, yeni çözümler seçili olan projeyi başlangıç projesi olarak kullanır.

 **MSBuild proje derlemesi çıkış ayrıntı düzeyi** Derleme için **Çıkış** penceresinde ne kadar bilgi görüntüleneceğini belirler.

 **MSBuild proje derleme günlük dosyası ayrıntı düzeyi**
 > [!NOTE]
> Bu seçenek yalnızca görsel C++ projeler için geçerlidir.

 @No__t_0 konumunda bulunan derleme günlüğü dosyasına ne kadar bilgi yazıldığını belirler... \\*ProjectName*\debug \\*ProjectName*. log.

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
