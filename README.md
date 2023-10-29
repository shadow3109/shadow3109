
import pygame
import random

# Inicjalizacja <link>Pygame</link>
pygame.init()

# Ustawienia planszy
szerokosc_planszy = 800
wysokosc_planszy = 600
rozmiar_klocka = 30

# Kolory
BIALY = (255, 255, 255)
CZARNY = (0, 0, 0)
CZERWONY = (255, 0, 0)
ZIELONY = (0, 255, 0)
NIEBIESKI = (0, 0, 255)
ZOLTY = (255, 255, 0)
FIOLETOWY = (255, 0, 255)
POMARANCZOWY = (255, 165, 0)

# Inicjalizacja planszy
plansza = []
for wiersz in range(wysokosc_planszy // rozmiar_klocka):
    plansza.append([CZARNY] * (szerokosc_planszy // rozmiar_klocka))

# Funkcja rysująca planszę
def rysuj_plansze(plansza):
    for wiersz in range(len(plansza)):
        for kolumna in range(len(plansza[wiersz])):
            pygame.draw.rect(
                ekran,
                plansza[wiersz][kolumna],
                (kolumna * rozmiar_klocka, wiersz * rozmiar_klocka, rozmiar_klocka, rozmiar_klocka),
            )

# Główna pętla gry
while True:
    # Obsługa zdarzeń
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # Aktualizacja planszy
    plansza = [[random.choice([CZARNY, CZERWONY, ZIELONY, NIEBIESKI, ZOLTY, FIOLETOWY, POMARANCZOWY]) for _ in range(szerokosc_planszy // rozmiar_klocka)] for _ in range(wysokosc_planszy // rozmiar_klocka)]

    # Rysowanie planszy
    ekran.fill(BIALY)
    rysuj_plansze(plansza)
    pygame.display.update()
    
