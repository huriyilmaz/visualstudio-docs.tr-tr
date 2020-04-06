---
title: IDebugProcess3::Yürüt | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723685"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Bu işlemi durdurulan bir durumdan çalıştırmaya devam ediyor. Önceki yürütme durumu (adım gibi) temizlenir ve işlem yeniden yürütmeye başlar.

> [!NOTE]
> Bu yöntem [Yürüt yerine](../../../extensibility/debugger/reference/idebugprogram2-execute.md)kullanılmalıdır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
[içinde] İş parçacığı yürütmek için temsil eden bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı, başka bir işlemin iş parçacığında durdurulmuş bir durumdan yürütmeye başladığında, bu yöntem bu işleme çağrılır. Kullanıcı IDE'deki **Hata Ayıklama** menüsünden **Başlat** komutunu seçtiğinde bu yöntem de çağrılır. Bu yöntemin uygulanması, işlemdeki geçerli iş parçacığıüzerinde [Devam](../../../extensibility/debugger/reference/idebugthread2-resume.md) yöntemini çağırmak kadar basit olabilir.

> [!WARNING]
> Bu aramayı işlerken Bir durdurma olayını veya [olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) anına anında (eşzamanlı) bir olay göndermeyin; aksi takdirde hata ayıklama asılabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sürdür](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
