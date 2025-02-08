#include "raylib.h"

#define KOREAN_COUNT 11172   // U+AC00 (44032) ~ U+D7A3 (55203) 의 글자 수

int main(void)
{
    InitWindow(800, 600, "raylib - 심재창 출력");

    const char* fontPath = "C:\\Windows\\Fonts\\malgun.ttf";
    int fontSize = 32;
    int glyphs[KOREAN_COUNT];
    for (int i = 0; i < KOREAN_COUNT; i++) glyphs[i] = 0xAC00 + i;

    Font font = LoadFontEx(fontPath, fontSize, glyphs, KOREAN_COUNT);

    // 3초 동안 실행 (창을 닫으면 바로 종료)
    double startTime = GetTime();
    while (!WindowShouldClose() && (GetTime() - startTime < 3.0))
    {
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawTextEx(font, "심재창", (Vector2) { 350, 280 }, fontSize, 1, BLACK);
        EndDrawing();
    }

    UnloadFont(font);
    CloseWindow();

    return 0;
}
