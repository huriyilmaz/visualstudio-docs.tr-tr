---
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 623cdd74b086a46bc52c0f0534953ae6e11168ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547396"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

. Exe/. dll dosyasıyla ilişkili hata ayıklama verilerini açar ve hazırlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 yürütülür  
 'ndaki . Exe veya. dll dosyasının yolu.  
  
 searchPath  
 'ndaki Hata ayıklama verilerini aramak için alternatif yol.  
  
 pCallback  
 'ndaki Bir `IUnknown` hata ayıklama geri [çağırması](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [ıdareadexeatoffsetcallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)ve/veya [ıdareadexeatrboş allback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri gibi bir hata ayıklama geri çağırma arabirimini destekleyen bir nesne için arabirim.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda, bu yöntem için olası hata kodlarının bazıları gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Dosya açılamadı veya dosya geçersiz bir biçime sahip.|  
|E_PDB_FORMAT|Eski biçimdeki bir dosyaya erişme girişiminde bulunuldu.|  
|E_PDB_INVALID_SIG|İmza eşleşmiyor.|  
|E_PDB_INVALID_AGE|Yaş eşleşmiyor.|  
|E_INVALIDARG|Geçersiz parametre.|  
|E_UNEXPECTED|Veri kaynağı zaten hazırlandı.|  
  
## <a name="remarks"></a>Açıklamalar  
 . Exe/. dll dosyasının hata ayıklama üst bilgisi, ilişkili hata ayıklama veri konumunu adlandırır.  
  
 Bu yöntem hata ayıklama üstbilgisini okur ve hata ayıklama verilerini arar ve hazırlar. Aramanın ilerleme durumu isteğe bağlı olarak, geri çağrılar aracılığıyla raporlanabilmesi ve denetlenemeyebilir. Örneğin, yöntem bir hata ayıklama dizini bulduğunda ve işlediğinde, [ıaloadcallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) çağrılır `IDiaDataSource::loadDataForExe` .  
  
 [Iareaareadexeatoffsetcallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) ve [ıseareadexeatrboş allback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) arabirimleri, bir dosyaya doğrudan standart dosya g/ç aracılığıyla erişilebilmesi durumunda, istemci uygulamanın yürütülebilir dosyadan veri okumak için alternatif yöntemler sağlamasına izin verir.  
  
 Bir. pdb dosyasını doğrulama olmadan yüklemek için [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metodunu kullanın.  
  
 . Pdb dosyasını belirli ölçütlere karşı doğrulamak için [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metodunu kullanın.  
  
 Bir. pdb dosyasını doğrudan bellekten yüklemek için [IDiaDataSource:: Loaddatafromistreaı](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metodunu kullanın.  
  
## <a name="example"></a>Örnek  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Ialoadcallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
