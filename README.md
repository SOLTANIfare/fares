# fares
Chess
كتابة كود لعبة شطرنج كاملة بلغة C++ يمكن أن يكون مشروعًا كبيرًا ومعقدًا، ولكن يمكننا تقديم مثال بسيط لكود يوضح الأساسيات. هذا المثال سيشمل بناء لوحة الشطرنج، وتحريك القطع، والتحقق من الحركات القانونية بشكل بسيط.

### متطلبات اللعبة
- **لوحة الشطرنج:** مصفوفة 8x8.
- **القطع:** سيتم تمثيلها باستخدام الأحرف، مثل `P` للجندي الأبيض و`p` للجندي الأسود، `R` للقلعة البيضاء و`r` للقلعة السوداء، وهكذا.
- **تحريك القطع:** نظام بسيط لتحريك القطع من مكان إلى آخر.
- **التأكد من الحركات القانونية:** سنقوم بتبسيط هذا الجزء لتوضيح الفكرة.

### كود اللعبة
الكود التالي هو مثال بسيط جداً ولا يغطي جميع القواعد الخاصة بلعبة الشطرنج، ولكنه يوفر الأساسيات لبدء تطوير اللعبة.

```cpp
#include <iostream>
#include <vector>
#include <string>

using namespace std;

// تعريف لوحة الشطرنج 8x8
vector<vector<char>> board = {
    {'R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R'},
    {'P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'},
    {' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '},
    {' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '},
    {' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '},
    {' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '},
    {'p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'},
    {'r', 'n', 'b', 'q', 'k', 'b', 'n', 'r'}
};

// دالة لطباعة لوحة الشطرنج
void printBoard() {
    for (int i = 0; i < 8; i++) {
        for (int j = 0; j < 8; j++) {
            cout << board[i][j] << " ";
        }
        cout << endl;
    }
}

// دالة لتحريك القطع
bool movePiece(string move) {
    int fromX = move[1] - '1';
    int fromY = move[0] - 'a';
    int toX = move[3] - '1';
    int toY = move[2] - 'a';

    // تحقق من أن الحركة داخل حدود اللوحة
    if (fromX < 0 || fromX >= 8 || fromY < 0 || fromY >= 8 || toX < 0 || toX >= 8 || toY < 0 || toY >= 8) {
        cout << "حركة غير صالحة!" << endl;
        return false;
    }

    // نقل القطعة
    board[toX][toY] = board[fromX][fromY];
    board[fromX][fromY] = ' ';
    return true;
}

int main() {
    string move;
    while (true) {
        printBoard();
        cout << "أدخل حركتك (مثل e2e4): ";
        cin >> move;
        if (move == "exit") break;
        if (movePiece(move)) {
            cout << "تم تحريك القطعة!" << endl;
        } else {
            cout << "حركة غير صالحة، حاول مرة أخرى." << endl;
        }
    }
    return 0;
}
```

### شرح الكود:
1. **تعريف لوحة الشطرنج:** يتم إنشاء مصفوفة 8x8 تحتوي على القطع المختلفة. الأحرف الكبيرة تمثل القطع البيضاء والصغيرة تمثل القطع السوداء.
2. **دالة `printBoard`:** تطبع اللوحة على الشاشة.
3. **دالة `movePiece`:** تنقل القطعة من مكان إلى آخر بعد التحقق من أن الحركة داخل حدود اللوحة.
4. **الدالة الرئيسية `main`:** تستمر في طلب الحركات من المستخدم حتى يكتب "exit". بعد كل حركة، تتم طباعة اللوحة.

### ملاحظات:
- هذا الكود بسيط للغاية ولا يتعامل مع جميع قواعد الشطرنج مثل التحقق من الحركات القانونية، التحقق من الشيك، الشيك مات، التبييت، الترقيات، إلخ.
- يمكن تحسين الكود بإضافة هذه القواعد والميزات لجعل اللعبة أكثر اكتمالاً.

إذا كنت ترغب في تطوير اللعبة بشكل أكبر، يمكنك البدء من هنا وإضافة المزيد من الوظائف.
