#!/usr/bin/python

import os
import sys

memory_list = []


def load(path):
    if not os.path.exists(path):
        print("not found %s" % path)
        exit(-1)
    with open(path, 'r') as f:
        for line in f:
            line = line.replace("\n", "").strip()
            memory_list.append(line)


def handle_line(line):
    for k in memory_list:
        if line.startswith(k):
            return True
    return False


if __name__ == "__main__":
    if len(sys.argv) != 4:
        print("Usage:python %s prefix_list src_file dst_file" % sys.argv[0])
        exit(-1)
    memory_path = sys.argv[1]
    source_path = sys.argv[2]
    dst_path = sys.argv[3]
    load(memory_path)
    if not os.path.exists(source_path):
        print("not found %s or %s" % (source_path, dst_path))
        exit(-1)
    idx = 0
    suc = 0
    with open(source_path, 'r') as f, open(dst_path, 'w') as of:
        for line in f:
            idx += 1
            # line = line.replace("\n", "")
            if not line:
                continue
            if handle_line(line):
                of.write(line)
                suc += 1
            if idx % 1000 == 0:
                print("handled %d records" % idx)
    print("over,total count:%d,match count:%d" % (idx, suc))
    exit(0)
