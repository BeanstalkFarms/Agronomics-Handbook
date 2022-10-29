# Fundraiser Facet

## Call Functions

### Fund

```solidity
function fund(
    uint32 id,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant returns (uint256);
```

### Create Fundraiser

```solidity
function createFundraiser(
    address payee,
    address token,
    uint256 amount
) external payable;
```

## View Functions

```solidity
function remainingFunding(uint32 id) public view returns (uint256);
}

function totalFunding(uint32 id) public view returns (uint256);

function fundingToken(uint32 id) public view returns (address);

function fundraiser(uint32 id)
    public
    view
    returns (Storage.Fundraiser memory);

function numberOfFundraisers() public view returns (uint32);
```

## Events

```solidity
event CreateFundraiser(
    uint32 indexed id,
    address fundraiser,
    address token,
    uint256 amount
);

event FundFundraiser(
    address indexed account,
    uint32 indexed id,
    uint256 amount
);

event CompleteFundraiser(uint32 indexed id);
```
