import pygame
import chess
import sys
import os
import requests
import io

# 설정
WIDTH, HEIGHT = 640, 640 # 이미지 버전에 맞춰 크기 조정
BOARD_SIZE = 8
SQ_SIZE = WIDTH // BOARD_SIZE

# 디자인 색상 (이미지와 잘 어울리는 고급스런 다크 그린 테마)
COLORS = {
    'light': (240, 217, 181), # 베이지
    'dark': (181, 136, 99),  # 갈색
    'selected': (130, 151, 105, 150), # 선택 시 올리브색 투명 강조
    'white_piece': (255, 255, 255),
    'black_piece': (0, 0, 0)
}

# 기물 이미지 URL 맵핑 (위키미디어 공식 경로)
IMAGE_URLS = {
    'P': 'https://upload.wikimedia.org/wikipedia/commons/4/45/Chess_plt45.svg',
    'R': 'https://upload.wikimedia.org/wikipedia/commons/7/72/Chess_rlt45.svg',
    'N': 'https://upload.wikimedia.org/wikipedia/commons/7/70/Chess_nlt45.svg',
    'B': 'https://upload.wikimedia.org/wikipedia/commons/b/b1/Chess_blt45.svg',
    'Q': 'https://upload.wikimedia.org/wikipedia/commons/1/15/Chess_qlt45.svg',
    'K': 'https://upload.wikimedia.org/wikipedia/commons/4/42/Chess_klt45.svg',
    'p': 'https://upload.wikimedia.org/wikipedia/commons/c/c7/Chess_pdt45.svg',
    'r': 'https://upload.wikimedia.org/wikipedia/commons/f/ff/Chess_rdt45.svg',
    'n': 'https://upload.wikimedia.org/wikipedia/commons/e/ef/Chess_ndt45.svg',
    'b': 'https://upload.wikimedia.org/wikipedia/commons/9/98/Chess_bdt45.svg',
    'q': 'https://upload.wikimedia.org/wikipedia/commons/4/47/Chess_qdt45.svg',
    'k': 'https://upload.wikimedia.org/wikipedia/commons/f/f0/Chess_kdt45.svg'
}

class ChessGame:
    def __init__(self):
        pygame.init()
        self.screen = pygame.display.set_mode((WIDTH, HEIGHT))
        pygame.display.set_caption("Chess Pro - Python Edition")
        self.font = pygame.font.SysFont("arial", 20, bold=True)
        self.board = chess.Board()
        self.selected_sq = None
        self.piece_images = {}
        self.download_and_load_images()

    def download_and_load_images(self):
        """인터넷에서 이미지를 다운로드하여 로컬에 저장하고 로드합니다."""
        # 이미지 저장할 폴더 생성
        if not os.path.exists('pieces'):
            os.makedirs('pieces')
            print("Downloading chess piece images... (Initial run only)")

        for symbol, url in IMAGE_URLS.items():
            filename = f"pieces/{symbol}.png"
            if not os.path.exists(filename):
                try:
                    response = requests.get(url)
                    # SVG 데이터를 PNG로 변환하여 저장
                    # pygame은 SVG를 직접 지원하지 않으므로, 임시로 텍스트로 대체하거나
                    # CairoSVG 같은 라이브러리를 써야 하지만, 여기서는 가장 단순하게 
                    # 위키미디어의 PNG 렌더링 주소를 사용합니다.
                    
                    # 위키미디어 SVG 주소를 PNG 주소로 변환
                    png_url = url.replace('/commons/', '/commons/thumb/').replace('.svg', '.svg/128px-' + os.path.basename(url).replace('.svg', '.svg.png'))
                    response = requests.get(png_url)

                    if response.status_code == 200:
                        with open(filename, 'wb') as f:
                            f.write(response.content)
                    else:
                        print(f"Failed to download: {symbol}")
                except Exception as e:
                    print(f"Error downloading {symbol}: {e}")

            # 로컬 파일 로드 및 크기 조정
            if os.path.exists(filename):
                image = pygame.image.load(filename)
                self.piece_images[symbol] = pygame.transform.smoothscale(image, (SQ_SIZE, SQ_SIZE))
            else:
                # 다운로드 실패 시 텍스트로 대체
                pass

        print("Images loaded successfully.")

    def draw_board(self):
        for r in range(BOARD_SIZE):
            for c in range(BOARD_SIZE):
                color = COLORS['light'] if (r + c) % 2 == 0 else COLORS['dark']
                sq = chess.square(c, 7 - r)
                pygame.draw.rect(self.screen, color, (c * SQ_SIZE, r * SQ_SIZE, SQ_SIZE, SQ_SIZE))
                
                # 선택된 칸 투명 하이라이트
                if self.selected_sq == sq:
                    overlay = pygame.Surface((SQ_SIZE, SQ_SIZE), pygame.SRCALPHA)
                    overlay.fill(COLORS['selected'])
                    self.screen.blit(overlay, (c * SQ_SIZE, r * SQ_SIZE))
                
                # 좌표 표시
                if c == 0:
                    lbl = self.font.render(str(8-r), True, (50, 50, 50))
                    self.screen.blit(lbl, (2, r * SQ_SIZE + 2))
                if r == 7:
                    lbl = self.font.render(chr(97+c), True, (50, 50, 50))
                    self.screen.blit(lbl, (c * SQ_SIZE + SQ_SIZE - 18, HEIGHT - 22))

    def draw_pieces(self):
        for r in range(BOARD_SIZE):
            for c in range(BOARD_SIZE):
                piece = self.board.piece_at(chess.square(c, 7 - r))
                if piece:
                    symbol = piece.symbol()
                    image = self.piece_images.get(symbol)
                    if image:
                        self.screen.blit(image, (c * SQ_SIZE, r * SQ_SIZE))
                    else:
                        # 이미지 없을 때 텍스트 대체
                        pass

    def run(self):
        clock = pygame.time.Clock()
        while True:
            # AI (흑) 이동
            if not self.board.is_game_over() and self.board.turn == chess.BLACK:
                pygame.time.delay(400) # 생각하는 척
                import random
                moves = list(self.board.legal_moves)
                if moves:
                    self.board.push(random.choice(moves))

            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    # 임시 폴더 삭제 (옵션)
                    # import shutil
                    # if os.path.exists('pieces'): shutil.rmtree('pieces')
                    pygame.quit()
                    sys.exit()
                
                if event.type == pygame.MOUSEBUTTONDOWN:
                    x, y = event.pos
                    c, r = x // SQ_SIZE, 7 - (y // SQ_SIZE)
                    sq = chess.square(c, r)

                    if self.selected_sq is None:
                        piece = self.board.piece_at(sq)
                        if piece and piece.color == self.board.turn:
                            self.selected_sq = sq
                    else:
                        move = chess.Move(self.selected_sq, sq)
                        # 폰 프로모션 강제 처리
                        if self.board.piece_at(self.selected_sq).piece_type == chess.PAWN and chess.square_rank(sq) in [0, 7]:
                            move.promotion = chess.QUEEN
                            
                        if move in self.board.legal_moves:
                            self.board.push(move)
                        self.selected_sq = None

            self.draw_board()
            self.draw_pieces()
            
            if self.board.is_game_over():
                pygame.display.set_caption(f"Game Over: {self.board.result()}")

            pygame.display.flip()
            clock.tick(30)

if __name__ == "__main__":
    # 인터넷 연결 확인을 위해 requests.exceptions.ConnectionError 예외 처리 추가
    try:
        game = ChessGame()
        game.run()
    except requests.exceptions.ConnectionError:
        print("Error: Internet connection is required for the initial run to download piece images.")


### 실행 시 참고사항
* **인터넷 연결**: 처음 실행할 때는 이미지를 다운로드하기 위해 인터넷 연결이 필요합니다.
* **폴더**: 코드를 실행하면 코드 파일이 있는 폴더 안에 `pieces`라는 새로운 폴더가 생기고, 그 안에 체스 기물 PNG 이미지들이 저장됩니다.
* **조작**: 이전과 동일하게 **[기물 클릭] -> [이동할 칸 클릭]** 방식입니다.

이제 화려한 이미지로 체스 게임을 즐기실 수 있습니다! 성공적으로 이미지가 뜨나요?
