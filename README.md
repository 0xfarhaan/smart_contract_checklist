# Smart contract checklist

Variables<br>
V1 - Is visibility set (SWC-108) <br>
V2 - Can they be private? <br>
V3 - Can it be constant?<br>
V4 - Can it be immutable?<br>
V5 - No unused variables (SWC-131)<br>

Structs<br>
S1 - Are the members split on 256 boundaries<br>
S2 - Can any members be a smaller type<br>

Functions<br>
F1 - Set visibility: Change external to public to support batching. Should it be private? (SWC-100)<br>
F2 - Should it be payable?<br>
F3 - Can it be combined with another similar function?<br>
F4 - Check behaviour for all function arguments when wrong or extreme<br>
F5 - Checks-Effects-Interactions pattern followed? (SWC-107)<br>
F6 - Check for front-running possibilities, such as the approve function (SWC-114)<br>
F7 - Avoid Insufficient gas grieving (SWC-126)?<br>
F8 - Gas Limit DoS via Block Stuffing<br>
F9 - Are the correct modifiers applied, such as onlyOwner<br>
F10 - Return arguments are always assigned<br>

Modifiers<br>
M1 - No state changes (except for a reentrancy lock)<br>
M2 - No external calls<br>
M3 - Checks only<br>
M4 - Are any unbounded loops/arrays used that can cause DoS? (SWC-128)<br>
M5 - Check behaviour for all function arguments when wrong or extreme<br>

Code<br>
C1 - All math done through BoringMath (SWC-101)<br>
C2 - Are any storage slots read multiple times?<br>
C3 - Are any unbounded loops/arrays used that can cause DoS? (SWC-128)<br>
C4 - Use block.timestamp only for long intervals (SWC-116)<br>
C5 - Don't use block.number for elapsed time (SWC-116)<br>
C6 - Don't use assert, tx.origin, address.transfer(), address.send()  (SWC-115 SWC-134 SWC-110)<br>
C7 - delegatecall only used within the same contract, never external even if trusted (SWC-112)<br>
C8 - Don't use function types<br>
C9 - Don't use blockhash, etc for randomness (SWC-120)<br>
C10 - Protect signatures against replay, use nonce and chainId (SWC-121)<br>
C11 - All signatures strictly EIP-712 (SWC-117 SWC-122)<br>
C12 - abi.encodePacked can't contain variable length user input (SWC-133)<br>
C13 - Careful with assembly, don't allow any arbitrary use data (SWC-127)<br>
C14 - Don't assume a specific ETH balance (and token) (SWC-132)<br>
C15 - Avoid Insufficient gas grieving (SWC-126)?<br>
C16 - Private data ISN'T private (SWC-136)<br>
C17 - Don't use deprecated functions, they should turn red anyway (SWC-111)<br>
    (suicide, block.blockhash, sha3, callcode, throw, msg.gas, constant for view, var)<br>
C18 - Never shadow state variables (SWC-119)<br>
C19 - No unused variables (SWC-131)<br>
C20 - Is calculation on the fly cheaper than storing the value<br>
C21 - Are all state variables read from the correct contract: master vs. clone<br>
C22 - Is > or < or >= or <= correct<br>
C23 - Are logical operators correct ==, !=, &&, ||, !<br>
C24 - Always mul before div, unless mul could overflow.<br>
C25 - Magic numbers > define as constant with useful name.<br>

Calls in Functions<br>
X1 - Is the result checked and errors dealt with? (SWC-104)<br>
X2 - If there is an error, could it cause a DoS. Like balanceOf causing revert. (SWC-113)<br>
X3 - What if it uses all gas?<br>
X4 - Is an external contract call needed?<br>
X5 - Is a lock used? If so are the external calls protected?<br>

Staticcalls(view) in functions<br>
S1 - Is it actually marked as view in the interface<br>
S2 - If there is an error, could it cause a DoS. Like balanceOf causing revert. (SWC-113)<br>
S3 - What if it uses all gas?<br>
S4 - Is an external contract call needed?<br>

Events<br>
E1 - Should any argument be indexed<br>

Contract<br>
T1 - Are all event there?<br>
T2 - Right-To-Left-Override control character not used, duh (SWC-130)<br>
T3 - No SELFDESTRUCT (SWC-106)<br>
T4 - Check for correct inheritance, keep it simple and linear (SWC-125)<br>

File<br>
P1 - SPDX header<br>
P2 - Solidity version hardcoded to 0.6.12 (SWC-102 SWC-103 SWC-124 SWC-129)<br>
P3 - Remove solhints that aren't needed<br>
