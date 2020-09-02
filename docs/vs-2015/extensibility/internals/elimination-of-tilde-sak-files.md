---
title: Eleme ~ SAK Files | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 751acf4e5f56b7b477f05ab71571e0becd566649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789593"
---
# <a name="elimination-of-sak-files"></a>~SAK Dosyalarının Ortadan Kaldırılması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API 1,2 ' de, ~ SAK dosyaları yetenek bayraklarıyla ve kaynak denetimi eklentisinin MSSCCPRJ dosyasını ve paylaşılan kullanıma alma işlemleri destekleyip desteklemediğini algılayan yeni işlevlerle değiştirilmiştir.  
  
## <a name="sak-files"></a>~ SAK dosyaları  
 Visual Studio .NET 2003 ön eki olan geçici dosyalar oluşturuldu ~ SAK. Bu dosyalar, bir kaynak denetimi eklentisinin destekleyip desteklemediğini tespit etmek için kullanılır:  
  
- MSSCCPRJ. SCC dosyası.  
  
- Çoklu (paylaşılan) kullanıma alma işlemleri.  
  
  Kaynak denetimi eklentisi API 1,2 ' de sunulan gelişmiş işlevleri destekleyen eklentiler için, IDE, aşağıdaki bölümlerde ayrıntılı olarak açıklanan yeni özellikleri, bayrakları ve işlevleri kullanarak geçici dosyaları oluşturmadan bu özellikleri algılayabilir.  
  
## <a name="new-capability-flags"></a>Yeni yetenek bayrakları  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>Yeni Işlevler  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Bir kaynak denetimi eklentisi çoklu (paylaşılan) kullanıma alma işlemleri destekliyorsa, `SCC_CAP_MULTICHECKOUT` özelliği bildirir ve `SccIsMultiCheckOutEnabled` işlevi uygular. Bu işlev, kaynak denetimli projelerin herhangi birinde bir kullanıma alma işlemi gerçekleştiğinde çağrılır.  
  
 Bir kaynak denetimi eklentisi bir MSSCCPRJ oluşturmayı ve kullanımını destekliyorsa. Bu durumda, `SCC_CAP_SCCFILE` özelliği bildirir ve [Sccwillcreatesccdosyasını](../../extensibility/sccwillcreatesccfile-function.md)uygular. Bu işlev, bir dosya listesi ile çağırılır. İşlevi, `TRUE/FALSE` Visual Studio 'nun BIR Mssccprj kullanması gerekip gerekmediğini belirtmek için her bir dosya için döndürür. Bu dosya için SCC dosyası. Kaynak denetimi eklentisi bu yeni özellikleri ve işlevleri desteklememe seçerse, bu dosyaların oluşturulmasını devre dışı bırakmak için aşağıdaki kayıt defteri anahtarını kullanabilir:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateTemporaryFilesInSourceControl" = DWORD: 00000001  
  
> [!NOTE]
> Bu kayıt defteri anahtarı DWORD: 00000000 olarak ayarlandıysa, varolmayan anahtarla eşdeğerdir ve Visual Studio yine de geçici dosyaları oluşturmaya çalışır. Ancak, kayıt defteri anahtarı DWORD: 00000001 olarak ayarlandıysa, Visual Studio geçici dosyaları oluşturmayı denemez. Bunun yerine, kaynak denetimi eklentisinin MSSCCPRJ desteklemediği varsayılmaktadır. SCC dosyası ve paylaşılan kullanıma alma işlemleri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
