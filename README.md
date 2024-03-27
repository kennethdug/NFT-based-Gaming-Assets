# NFT-based-Gaming-Assets
Intégrez les NFT dans les jeux vidéo, permettant aux joueurs de posséder, échanger et vendre des actifs de jeu uniques.
# Demo Python Code for NFT-based Gaming Assets

class Blockchain:
    def __init__(self):
        self.chain = []
        self.transactions = []
        self.create_block(proof=1, previous_hash='0')  # Genesis block

    def create_block(self, proof, previous_hash):
        block = {
            'index': len(self.chain) + 1,
            'proof': proof,
            'previous_hash': previous_hash,
            'transactions': self.transactions
        }
        self.transactions = []  # Reset the list of transactions after adding them to a block
        self.chain.append(block)
        return block

class NFT:
    def __init__(self, name, owner):
        self.name = name
        self.owner = owner

    def transfer_ownership(self, new_owner):
        self.owner = new_owner
        print(f'{self.name} now owned by {self.owner}')

class GameAsset(NFT):
    def __init__(self, name, owner, game_attributes):
        super().__init__(name, owner)
        self.game_attributes = game_attributes

def main():
    # Simulating a blockchain
    blockchain = Blockchain()
    
    # Creating NFT-based game assets
    sword = GameAsset(name="Excalibur", owner="Player1", game_attributes={"damage": 100, "magic": 50})
    potion = GameAsset(name="Healing Potion", owner="Player2", game_attributes={"heal": 50})
    
    # Transfer ownership of the NFT
    print("Before transfer:")
    print(f'{sword.name} is owned by {sword.owner}')
    
    sword.transfer_ownership("Player3")
    
    print("After transfer:")
    print(f'{sword.name} is owned by {sword.owner}')

if __name__ == "__main__":
    main()
