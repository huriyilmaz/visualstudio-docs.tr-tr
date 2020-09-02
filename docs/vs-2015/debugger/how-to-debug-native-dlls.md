---
title: "Nasıl yapılır: yerel dll 'Lerde hata ayıklama | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702673"
---
# <a name="how-to-debug-native-dlls"></a>Nasıl Yapılır: Yerel DLL'lerde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Bir DLL dosyasında hata ayıklarken, hata ayıklamayı başlatabilirsiniz:  
  
- DLL 'i çağıran yürütülebilir dosyayı oluşturmak için kullanılan proje.  
  
  \- veya  
  
- DLL kendisini oluşturmak için kullanılan proje.  
  
  Yürütülebilir dosyayı oluşturmak için kullanılan projeniz varsa, bu projeden hata ayıklamayı başlatın. Daha sonra DLL için bir kaynak dosyası açabilir ve çalıştırılabilir dosyayı oluşturmak için kullanılan projenin bir parçası olmasa bile bu dosyada kesme noktaları ayarlayabilirsiniz. Daha fazla bilgi için bkz. [kesme noktaları](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  DLL 'yi oluşturan projeden hata ayıklamayı başlatırsanız, DLL 'de hata ayıklama sırasında kullanmak istediğiniz yürütülebilir dosyayı belirtmeniz gerekir.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Hata ayıklama oturumu için yürütülebilir bir dosya belirtmek için  
  
1. **Çözüm Gezgini**, dll 'yi oluşturan projeyi seçin.  
  
2. **Görünüm** menüsünde**Özellik sayfaları**' nı seçin.  
  
3. **Özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörünü açın ve **hata ayıklama** kategorisini seçin.  
  
4. **Komut** kutusunda, kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. **Komut bağımsız değişkenleri** kutusunda, yürütülebilir dosya için gereken tüm bağımsız değişkenleri belirtin.  
  
   _Proje_**Özellik sayfaları** iletişim kutusunda çalıştırılabilir dosyasını belirtmezseniz, hata ayıklamaya başladığınızda [hata ayıklama oturumu için yürütülebilir iletişim kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
