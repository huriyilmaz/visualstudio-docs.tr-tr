---
title: 'Nasıl yapılır: ön ve araç sonrası komutları belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab7ecbe97ba0b174a1cc4c0f0d169834ce25e8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788909"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Nasıl yapılır: Ön ve Son İzleme Komutları Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir performans oturumunda ikili dosyalardan önce veya sonra çalıştırılan komutlar görüntülenir. Komut satırından verilebileceğiniz herhangi bir komut, bir ön izleme veya bir işaretleme sonrası olay olarak belirtilebilir. Örneğin, ikili dosyalar görüntülendikten sonra yürütülen bir toplu iş dosyasında tanımlayıcı ad anahtarı olan bir derlemenin çekilişini otomatikleştiren komutları belirtebilirsiniz.  
  
 Profil oluşturma çalıştırmasında veya tek tek ikili dosyalarda tüm belgelenmiş ikili dosyalar için komutlar belirtebilirsiniz. Ancak, daha önce çalıştırmak için yalnızca bir pre-Instrument komutu ve izleme işleminden sonra çalıştırılacak bir araç sonrası komutu belirtebilirsiniz. Tüm ikili dosyalar için ve tek tek ikililer için komut belirtemezsiniz. Tüm ikili dosyalar için komutlar belirttiğinizde, komutlar oturumdaki her bir ikilinin izleme öncesi veya sonrasında çalıştırılır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Komutların yürütüldüğü çalışma dizini, çalıştırdığınız [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ve profili oluşturulmuş uygulamanın hedef platformundaki işletim Sistel öğesine bağlıdır.  
  
  **32 bit bilgisayarlar**  
  
  32 bit bilgisayarlarda, varsayılan profil oluşturucu araçları dizini Drive\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools dizinidir.  
  
  **64 bit bilgisayarlar**  
  
  64 bit bilgisayarlarda, profili oluşturulmuş uygulamanın hedef platformuna göre yolu belirtin:  
  
- 32 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:  
  
   *Sürücü*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\performans araçları  
  
- 64 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:  
  
   *Sürücü*\Program Files (x86) \Microsoft Visual Studio 10.0 \ Team Tools\performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Araç öncesi komutları belirtmek için  
  
1. Aşağıdaki adımlardan birini uygulayın:  
  
    - Bir performans oturumunda tüm ikili dosyalar için ön gereç komutlarını belirtmek üzere **Performans Gezgini**' deki performans oturumu düğümünü seçin ve ardından **Özellikler**' i seçin.  
  
    - Belirli bir ikiliye ilişkin ön gereç komutlarını belirtmek için, performans oturumunun **hedefler** listesinden ikilinin adına sağ tıklayın ve ardından **Özellikler**' i seçin.  
  
2. **Özellik sayfalarında**, **izleme**' ye tıklayın.  
  
3. Komut **satırı** metin kutusuna komutu, **önceden işaretleme olayları**altında yazın.  
  
    > [!NOTE]
    > **Komut satırı** kutusunun yanındaki üç nokta düğmesini **(...)** tıklatarak uygun. exe,. cmd veya. bat dosyasına gözatıp seçebilirsiniz.  
  
4. **Tamam**’a tıklayın.  
  
     Komutun kaldırılmadan çalıştırılmasını devre dışı bırakmak için, **araçlardan Dışla** onay kutusunu seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için, proje özelliği sayfalarını kullanın.  
  
### <a name="to-specify-post-instrument-commands"></a>Araç sonrası komutları belirtmek için  
  
1. Aşağıdaki adımlardan birini uygulayın:  
  
    - Bir performans oturumunda tüm ikili dosyalar için araç sonrası komutları belirtmek için **Performans Gezgini**' deki performans oturumu düğümünü seçin ve ardından **Özellikler**' i seçin.  
  
    - Belirli bir ikiliye yönelik son araç komutlarını belirtmek için, performans oturumunun **hedefler** listesinden ikilinin adına sağ tıklayın ve ardından **Özellikler**' i seçin.  
  
2. **Özellik sayfalarında**, **izleme**' ye tıklayın.  
  
3. Komut **satırı** metin kutusuna komutu, **son izleme olayları**altında yazın.  
  
    > [!NOTE]
    > **Komut satırı** kutusunun yanındaki üç nokta düğmesini **(...)** tıklatarak uygun. exe,. cmd veya. bat dosyasına gözatıp seçebilirsiniz.  
  
4. **Tamam**’a tıklayın.  
  
     Komutun kaldırılmadan çalıştırılmasını devre dışı bırakmak için, **araçlardan Dışla** onay kutusunu seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için, proje özelliği sayfalarını kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Oturumlarını Yapılandırma](../profiling/configuring-performance-sessions.md)
